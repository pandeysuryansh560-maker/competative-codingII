Experiment 2.1
 
 39: Combination Sum

 class Solution {
public:
    void solve(vector<int>& candidates, int target,
               int index, vector<int>& current,
               vector<vector<int>>& result) {

        if (target == 0) {
            result.push_back(current);
            return;
        }
        if (target < 0 || index == candidates.size()) {
            return;
        }
        current.push_back(candidates[index]);
      solve(candidates, target - candidates[index],
              index, current, result);
        current.pop_back();
        solve(candidates, target,
              index + 1, current, result);
    }
    vector<vector<int>> combinationSum(vector<int>& candidates,
                                       int target) {
        vector<vector<int>> result;
        vector<int> current;
        solve(candidates, target, 0, current, result);
        return result;
    }
};


Experiment 2.2
236. Lowest Common Ancestor of a Binary Tree.

class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (root == NULL || root == p || root == q) {
            return root;
        }
        TreeNode* left = lowestCommonAncestor(root->left, p, q);
        TreeNode* right = lowestCommonAncestor(root->right, p, q);
        if (left != NULL && right != NULL) {
            return root;
        }
        return (left != NULL) ? left : right;
    }
};
