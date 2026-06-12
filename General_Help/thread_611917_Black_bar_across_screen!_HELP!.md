---
title: "Black bar across screen! HELP!"
date: 2007-11-13
forum: General Help
---

### Post by Sp1kez on 2007-11-13
After installing ubuntu 7.10 a black bar is across my screen taking up a big percentage of it, I had this problem while using liveCD as well, I looked into it and people have posted some  patches to fix this but when I run the package it tells me that a newer version is already installed, how do I override this and force the install?

here is some links to explaining the problem


[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/137604](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/137604)

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/137604](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/137604)

How do I get rid of this black bar across my screen?

---

### Post by jfinkels on 2007-11-13
From the first bug thread:> 
 IdleOne wrote on 2007-09-14:

to prevent xserver-xorg-core upgrade after downgrading to ubuntu2 put a hold on package xserver-xorg-core :
" sudo aptitude hold xserver-xorg-core " this will hold package to current installed version untill this bug is fixed ( SOON!? )


---

