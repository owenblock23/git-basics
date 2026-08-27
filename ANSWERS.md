# Git Quick Reference

Fill this in as you work through the studio. Write each explanation in your
own words — this is meant to be something you can print and keep as a
reference later, not a transcript of your terminal.

## Exercise 1 — Cloning a repo

**Command(s):** `git clone <url>`, `git status`

**Explanation:**

% git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

git status says that there are no necessary updates for my branch, as it is in sync with the original repo. The "clean" status means that there are no changes that are untracked in the workspace.

## Exercise 2 — Ignoring files

**Command(s):** `.gitignore`, `git status`

**Explanation:**
//
% ls -a
.               ANSWERS.md
..              README.md
.git            notes.txt
.gitignore      progress.txt
(base) oblock@Thanos-3 git-basics % cat .gitignore
# Build artifacts
*.log
*.o
*.obj
build/

# Editor / OS files
*.swp
.DS_Store
Thumbs.db
//

After creating build.log and important.txt, we see that there is an untracked file: important.txt. This occurs because the file does not match any of the artifacts included in the gitignore, and the changes are not synced across local and main branches.

The reason build.log is not included as an untracked file is because it is a .log which is included in the gitignore. Gitignore is used to create "exceptions" and cases where we don't have to worry about untracked changes.

## Exercise 3 — Viewing changes

**Command(s):** `git diff <file>`, `git diff`

**Explanation:**

git diff notes.txt

diff --git a/notes.txt b/notes.txt
index e4b7830..f80f9a9 100644
--- a/notes.txt
+++ b/notes.txt
@@ -2,3 +2,4 @@ Notes
 =====
 
 Use this file to jot down notes during the studio.
+Adding a note about today's studio.

git diff
diff --git a/notes.txt b/notes.txt
index e4b7830..f80f9a9 100644
--- a/notes.txt
+++ b/notes.txt
@@ -2,3 +2,4 @@ Notes
 =====
 
 Use this file to jot down notes during the studio.
+Adding a note about today's studio.
//
git diff shows the changes that have not yet been updated, as does git diff with the filename. I believe that adding the filename means that there is more specificity and you just are looking for the unsaved changes in that file.

## Exercise 4 — Undoing changes before staging

**Command(s):** `git restore <file>`

**Explanation:**

git restore file reverts the file to its previous state, meaning that you have no updates since the last time the branch was actually saved. 

This is risky because if you don't know when you last updated your project, using restore would mean you are reverting back to previous changes and losing your progress.

## Exercise 5 — Staging and committing

**Command(s):** `git add <file>`, `git commit -m "<message>"`

**Explanation:**

git add means that you add the file to the staging area, and git status checks to see what is staged vs untracked. 

A useful commit message has a specific subject and contextualizes the change instead of just naming it.

## Exercise 6 — Unstaging a change

**Command(s):** `git restore --staged <file>`

**Explanation:**

The worknig directory is what is happenign on your local device (can be unsaved), while your staging area is where changed items are ready to be saved, and then a commit is the actual action of updating the branch and sending the changes.

## Exercise 7 — Viewing history

**Command(s):** `git log --oneline`

**Explanation:**

76efe09 (HEAD -> main) Track studio progress notes
ec9dc44 Add reflection notes from git studio exercise 5
1634ee7 (origin/main, origin/HEAD) updated title
3352917 updated studio
c74883f updated
18b1c76 updated instructions
dbecb3e updated exercise 3
efdc976 updated overview
0e574ef updated title and instructions
a25c6de updated README
0653809 adding starter files
ae72925 Initial commit
//
Git log --oneline shows the commits that have been made in the past. This is useful for tracking changes over time.

## Exercise 8 — Undoing a commit safely

**Command(s):** `git revert <commit-hash>`

**Explanation:**

Git revert is safer to use because it is more modular and allows for more oversight compared to directly editing or removing commits directly.

## Exercise 9 — Pushing and syncing

**Command(s):** `git push`, `git fetch`

**Explanation:**

Git push pushes to the remote repository (saves changes), whle git fetch updates the local machine when others make changes to the remote repository.
