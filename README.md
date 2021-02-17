## Git Flow Example

The `master` branch should contain the latest and greatest code. Feature branches are created off `master` and then merged back when the features are complete (or have reached a good checkpoint). To get started: 

#### Submitting New Work**

Note:** Do **NOT** add GitHub modifiers to your commit messages like "Closes #5".  Your commits/branches will go through a review process and it's not possible to tell when an issue will really be closed until after the review is completed.

1. Clone the repo to your development machine: `git clone https://github.com/myrepo/myrepo.git`
1. The repo's issue board is used to track possible items to work.  Find an issue to work on the board, or create a new issue with some information about why the feature is needed.  It's useful to include information about who is requesting the feature it's someone other than yourself and information about the solution strategy.
1. Create your feature branch: `git checkout -b <issue_number>_my_feature`.  Feature branches should be linked back to an issue on the issue board by starting each branch name with an issue number.  For example, if your feature addresses issue number 5 which adds a new snazzy view helper, your branch name could be something like `5_add_snazzy_view_helper`.  The text that comes after the issue number doesn't have to be the exact time of the issue, but it should be something descriptive enough so people can quickly get an idea of what the feature branch is doing.
1. Implement your feature and tests.
1. Rebase your commits on top of the latest `master`.
1. Push the branch to the remote: `git push -u origin my_feature`.
1. Submit a Pull Request and assign someone to review the PR.  In the PR message, include whether or not this feature is completely done or if you intend to do more work.  Unless you indicate that you plan to do more work in the branch, it will be removed from the remote.  If your PR only partially addresses the feature, indicate what has been completed and what remains.  The will help the code reviewer understand where things stand.

#### Accepting Pull Requests 

**Note:** Do **NOT** add auto close GitHub modifiers like "Closes #5" to any commits.  The status of a commit should be tracked by manually moving the Issue into the appropriate status lane via the GitHub UI.  Issues are not closed when the code is merged into `master`; they are closed when someone has manually tested and verified they still work __after__ being merged into `master`.

1. Select the Pull Request you would like to work and read the description.  The PR description should indicate if the feature has been completely worked or if it just a partial solution.  You should also read the description of the issue.
1. Checkout `master` to make sure you have the latest: `git checkout master` then `git pull`.
1. Checkout the feature branch locally: `git checkout <issue_number>_the_feature`
1. Make sure the code is rebased.  Either get the author to rebase and resubmit, or rebase yourself and force push to the remote.  If you rebase yourself, make sure you tell the author so they can update on their end.  Also, make sure you force push `git push -f` so the PR will get updated.  If you fail to do this, the PR may not automatically update when you merge the branch later.
1. Review the code and make change requests as needed.
1. The feature branch should be rebased on the very latest master before attempting the merge.  Someone might have updated `master` while you were reviewing the code so checkout `master` and make sure you have the latest one more time: `git checkout master` then `git pull`.  Rebase the feature branch again if necessary and run the tests one more time.
1. Merge the branch into master: `git merge <issue_number>_the_feature --no-ff`.  Make sure `--no-ff` is used so a merge commit is created.   You will be asked for a merge commit message.  Add the following to the front of the messages `Support #<issue number> ` and replace `<issue number>` with the correct issue number.  The combination of `#` and a number will cause GitHub to add a message on the issue's page with a link to this merge commit.
1. Push `master` up to the remote: `git push`.
1. Check the message on the original PR and see if the work completes the feature.  If it does, remove the remote feature branch.
1. Go to the issue page and update the Pipeline field to reflect the new status of the Issue.
