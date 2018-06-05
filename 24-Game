NOTE: 
Each time, we create nums_ which is an empty vector and choose 2 elements
out of nums, perform one of the four operations and put the result back
to nums_ with the rest numbers in nums. We do this recursively until there
is only one element in nums, then we check is it 24.
parentheses: we choose 2 elements out from the vector to act like they
             are inside the parentheses.
             
Link on LeetCode: https://leetcode.com/problems/24-game/description/

```
class Solution {
public:
    bool judgePoint24(vector<int>& nums) {
        vector<double> nums_;
        for (int i = 0; i < 4; i++) nums_.push_back(nums[i]);
        return judge(nums_);
    }
    
    // nums passed by value
    bool judge(vector<double> nums) {
        if (nums.size() == 0) return false;
        if (nums.size() == 1) return abs(nums[0] - 24) < 1e-6;
        
        for (int i = 0; i < nums.size(); i++) {
            for (int j = 0; j < nums.size(); j++) {
                if (i == j) continue;
                double n1 = nums[i], n2 = nums[j];
                vector<double> nums_;
                // put the rest value in the nums into nums_
                for (int k = 0; k < nums.size(); k++) if (k != i && k != j) nums_.push_back(nums[k]);
                for (int k = 0; k < 4; k++) {
                    // prevent caculating n2 + n1 or n2 * n1 after caculating n1 + n2 or n1 * n2
                    if (j < i && k < 2) continue;
                    if (k == 0) nums_.push_back(n1 + n2);
                    if (k == 1) nums_.push_back(n1 * n2);
                    if (k == 2) nums_.push_back(n1 - n2);
                    if (k == 3 && n2 != 0) nums_.push_back(n1 / n2);
                    
                    if (judge(nums_)) return true;
                    // remove the element added to nums_ in this iteration
                    nums_.erase(nums_.end() - 1);
                }
            }
        }
        return false;
    }
};
```
 
