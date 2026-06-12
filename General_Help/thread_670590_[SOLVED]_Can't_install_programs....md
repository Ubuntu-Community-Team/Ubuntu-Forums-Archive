---
title: "[SOLVED] Can't install programs..."
date: 2008-01-17
forum: General Help
---

### Post by Reaper89 on 2008-01-17
Hi, i'm quite new to linux but i do know a bit, anyway i have Ubuntu 7.10 (x86 Desktop Edition)) and when i go to Add/Remove Applications and search an application to install it says "The list of applications is not availabe" (just noticed they spelt it available wrong :p) "click on 'Reload' to load it. To reload the list you need a working internet connection." But the internet itself works perfectly, USB and Ethernet.

Any ideas will be greatly appreciated

---

### Post by p_quarles on 2008-01-17
It's possible that the list of repositories got disabled somehow. The easiest way to find out is to open a terminal, and run the following command:
```
cat /etc/apt/sources.list
```
If you could post the output here, we can determine if that's the problem (which will be easy to fix).

---

### Post by Reaper89 on 2008-01-17
> **p_quarles said:**
> It's possible that the list of repositories got disabled somehow. The easiest way to find out is to open a terminal, and run the following command:
```
cat /etc/apt/sources.list
```
If you could post the output here, we can determine if that's the problem (which will be easy to fix).

josh@josh-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by p_quarles on 2008-01-17
Is it possible that you weren't connected to the internet during the installation process? 

Anyway, editing that file should fix the problem. First, open it up with root privileges (otherwise it won't let you save changes):
```
gksudo gedit /etc/apt/sources.list
```
Now, remove the comment symbol ("#") from the beginning of the lines that start with "deb" and "deb-src." 

Technically, you don't *need* to uncomment the lines that end with "universe,"  "multiverse," and "partner" -- but they contain a lot of popular software, so you might as well. 

Once you're done, save it, and run the graphical package manager again. Post back if it gives you more of the same problem.

---

### Post by Reaper89 on 2008-01-17
> **p_quarles said:**
> Is it possible that you weren't connected to the internet during the installation process? 

Anyway, editing that file should fix the problem. First, open it up with root privileges (otherwise it won't let you save changes):
```
gksudo gedit /etc/apt/sources.list
```
Now, remove the comment symbol ("#") from the beginning of the lines that start with "deb" and "deb-src." 

Technically, you don't *need* to uncomment the lines that end with "universe,"  "multiverse," and "partner" -- but they contain a lot of popular software, so you might as well. 

Once you're done, save it, and run the graphical package manager again. Post back if it gives you more of the same problem.

Well i had my wireless adapter plugged in during install so that was probably why. What you said worked perfectly thanks very much :D

---

