
(starting with a nearly blank project repo)
git clone https://github.com/spe-bfountain/test_bf_908gits_main1 proj1

(subtrees: make a new remote -- NOTE: there must be at least 1 commit in proj1 first!)
cd proj1
git remote add -f dry https://github.com/spe-bfountain/test_bf_908gits_common.git

(subtrees: add from that remote to a new subtree in the current project)
git subtree add --prefix dry dry master --squash


(subtrees: pull before each time you want to change common code from within a project)
git subtree pull --prefix dry dry master


(subtrees: go from the project repo into the dir checked out from the common repo, make a change)
cd dry ;# be sure to only do this committing from INSIDE the common area
touch new4common ; git add new4common ; git commit -m "new file from project to common" new4common
cd ..
git push origin master ;# be sure to only do this pushing from OUTSIDE the common area
git subtree push --prefix dry dry master



(subtrees: pull all the changes into the common repo)
cd ../common ;
git pull origin master


