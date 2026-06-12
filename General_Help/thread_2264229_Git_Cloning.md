---
title: "Git Cloning"
date: 2015-02-06
forum: General Help
---

### Post by Matthew_Harrop on 2015-02-06
When I clone my git repository on my server I only get the currently selected working branch in the repository rather than all the branches. I want to pull down ALL the branches (As a sort-of local back up against disaster) does anybody know how to force clone to bring down everything?

Just for transparency i use this command to clone:

> 
sudo git clone ssh://<username>@<Servername>:<Port>/git/<ProgramName>/app/<GitRepository.git>


There are 8 branches (Including master)
They all contain slightly different off-shoots of the same program, so i lumped them all together in the same repository

I have double checked the cloned repository for the branches and it only displays the currently selected one.

EDIT: Sorry, I found my answer: 
[http://stackoverflow.com/questions/67699/clone-all-remote-branches-with-git](http://stackoverflow.com/questions/67699/clone-all-remote-branches-with-git)

JIC The link dies: 
> 
 First, clone a remote [Git]("http://en.wikipedia.org/wiki/Git_%28software%29") repository and [cd]("http://en.wikipedia.org/wiki/Cd_%28command%29") into it:
  $ git clone git://example.com/myproject
$ cd myproject
  Next, look at the local branches in your repository:
  $ git branch
* master
  But there are other branches hiding in your repository! You can see these using the -a flag:
  $ git branch -a
* master
  remotes/origin/HEAD
  remotes/origin/master
  remotes/origin/v1.0-stable
  remotes/origin/experimental
  If you just want to take a quick peek at an upstream branch, you can check it out directly:
  $ git checkout origin/experimental
  But if you want to work on that branch, you'll need to create a local tracking branch:
  $ git checkout -b experimental origin/experimental
  and you will see
  Branch experimental set up to track remote branch experimental from origin.
Switched to a new branch 'experimental'
  That last line throw some people "New branch" - huh? What it really means is a new local branch that gets the branch from the index and creates it locally for you.  The *previous*  line is actually more informative as it tells you that the branch is  being set up to track the remote branch, which usually means the  origin/branch_name branch 
  Now, if you look at your local branches, this is what you'll see:
  $ git branch
* experimental
  master
  You can actually track more than one remote repository using git remote.
  $ git remote add win32 git://example.com/users/joe/myproject-win32-port
$ git branch -a
* master
  remotes/origin/HEAD
  remotes/origin/master
  remotes/origin/v1.0-stable
  remotes/origin/experimental
  remotes/win32/master
  remotes/win32/new-widgets
  At this point, things are getting pretty crazy, so run gitk to see what's going on:
  $ gitk --all &
     



---

