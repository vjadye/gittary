# Summary
These are most the git commands I used most commonly in my dev workflow.

# Handy git commands to manage your commits ###

1. Show files in your commit
Use case: Accidentally commited some cruft? Look at your commit and then remove any files that do not belong there.

Option 1

`git show --name-only $COMMIT_HASH`

Option 2

`git diff-tree --no-commit-id --name-only $COMMIT_HASH -r`

2. Remove unwanted file from a local commit


3. Collapse multiple local commits
Use case: Cherry picked several commits from a dev-branch or merged a dev branch to mainline? You may have multiple commits that you may decide to eventually push as a single commit.

`git rebase -i` and change `pick` to `squash` in front of the newer commits. Save the file and continue with squashing.

4. Append changes to a local commit
Use case: You realize that an additional change is required to your commit based on testing or code review feedback.

```
git add --all // or necessary files
git commit --amend --no-edit // remove --no-edit if you need to update the commit message.
```

5. Create a patch
Use case: copy changes from a working tree to another working tree from same repo. Or share your local commit with another team member without pushing it to a branch.

In your workspace,
`git diff > patch.txt`

Apply the patch to a new working tree
`git apply patch.txt`