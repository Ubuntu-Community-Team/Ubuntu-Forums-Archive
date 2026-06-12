---
title: "Having an issue installing Backtrack Repo under Ubuntu 12.10?"
date: 2013-03-23
forum: General Help
---

### Post by Moose on 2013-03-23
Hey guys. I am trying to add the Backtrack Repo to Ubuntu 12.10. And I am using [these instructions.]("http://xtrabuntu.blogspot.com.au/2012/10/how-to-add-backtrack-repository-to.html") But whenever I run *Sudo Apt-Get Update*, I get this:

```
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/main i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_main_binary-i386_Packages)W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/microverse i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_microverse_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/non-free i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/testing i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_testing_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/main i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_main_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/microverse i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_microverse_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/non-free i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/testing i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_testing_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/main i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_main_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/microverse i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_microverse_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/non-free i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://all.repository.backtrack-linux.org/ revolution/testing i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_testing_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems



```

And then the repo doesn't get added correctly and I can't install the Backtrack applications. Any help would be lovely.

---

### Post by Cheesemill on 2013-03-23
Don't do it.

Packages in the BackTrack repos are built for a completely different version of Ubuntu. Adding the BackTrack repositories to a Ubuntu 12.10 system is sure fire way to break your installation.

---

### Post by haqking on 2013-03-23
> **Cheesemill said:**
> Don't do it.

Packages in the BackTrack repos are built for a completely different version of Ubuntu. Adding the BackTrack repositories to a Ubuntu 12.10 system is sure fire way to break your installation.

+ 100000

BT is a specialist distro built for purpose, use it if you want it but dont try to build it.

It is not meant for day to day desktop use, it is meant specifically for a given task.

The same applies to when people install backtrack and then try to add Ubuntu repose to add al the latest software, it is not meant for that.

Besides BT is now slowly retiring as will the repos, Kali-linux is the replacement.

To the OP, yiou have asked a few similar questions now, just download BT and install it into a VM or use a Live USB/DVD as that is the way it is meant to be used or dual boot if you want an install.  BT wont do anything itself, you need to use to learn the tolls within it and have a reason too use them or test environment to do so.

Peace

---

