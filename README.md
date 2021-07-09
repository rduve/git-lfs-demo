# git-lfs-demo
Demo Repo for Git LFS.  Ryan will use this to demonstrate how to use Git LFS with big files.

Fork the repo, then clone it.

## Get the repo.
    git clone https://github.com/<your_name>/git-lfs-demo.git
    cd git-lfs-demo/
    
## Make a big file and track with Git LFS.
    git checkout -b make_data_file
    seq 1000000 > big_file.dat
    git-lfs track big_file.dat
    
## Push to server.
    git add .gitattributes
    git add big_file.dat
    git commit -m "Added big file."
    git push origin make_data_file

Be sure to go complete the PR on Github.
    
## Make new branch to change file.
    git checkout main
    git branch -D make_data_file
    git pull
    git checkout -b change_data_file
    
Change the file however you want.  I moved some rows around using `vim`.

## Push the changed file.
    git diff
    git add big_file.dat
    git commit -m "Changed big file."
    git push origin change_data_file

DO NOT complete this PR on Github, yet.

## Clone a new version of the repo and make a conflicting change.
    cd /tmp
    git clone https://github.com/<your_name>/git-lfs-demo.git
    mv git-lfs-demo/ git-lfs-demo_KYLE
    cd git-lfs-demo_KYLE
    git checkout -b change_file_differently
    
Change the file in a different way, here.  I'm adding a header row.

## Push to Github to see merge conflict.
    git add -A
    git commit -m "Added a header to data file."
    git push origin change_file_differently
    
Open a PR to `main` and see the conflict.  Notice the diff uses Git LFS hashes and not the huge file contents.
