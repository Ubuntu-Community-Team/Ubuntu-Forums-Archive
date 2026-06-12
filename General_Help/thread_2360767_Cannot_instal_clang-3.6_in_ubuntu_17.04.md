---
title: "Cannot instal clang-3.6 in ubuntu 17.04"
date: 2017-05-08
forum: General Help
---

### Post by heaven009 on 2017-05-08
Helo,
Cannot install Clang-3.6. Need it to solve compiling problem while installing Unreal engine. I tried installing with clang version 4.0 but it fails. I found on other threads that clang version 3.6 can solve the issue with make command.

I attached both error code sample. Please help solving the issue.

```
sudo apt-get install clang-3.6
[sudo] password for heaven009: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package clang-3.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


```


Unreal engine make command error code.
```
sudo make SlateViewer 
bash "/home/heaven009/UnrealEngine-master/Engine/Build/BatchFiles/Linux/Build.sh" SlateViewer Linux Development  
Building SlateViewer...
Creating makefile for SlateViewer (no existing makefile)
Performing full C++ include scan (no include cache file)
Using gcc version '6.3.0' (string), 6 (major), 3 (minor), 0 (patch)
ERROR: This version of the engine can only be compiled by clang - refusing to register the Linux toolchain.
Makefile:393: recipe for target 'SlateViewer' failed
make: *** [SlateViewer] Error 5


```

---

### Post by Perfect Storm on 2017-05-08
It should be available through universe repositories (make sure it's enabled), or get it through here: [http://packages.ubuntu.com/search?keywords=clang](http://packages.ubuntu.com/search?keywords=clang)

Thread moved to General Help.

---

### Post by heaven009 on 2017-05-08
But, I cannot find the 3.6 version in synaptic pakage manager.

I tried to download from the link but i'm confused which one to install(maybe you can help)
downloaded the 3.6 deb pakage and tried to install using GDebi. but it says "dependency is not satisfiable" error.

My main goal is to install Unreal engine and still cannot solve the issue. Clang may not be the main issue. I may missing something.
I installed clang 3.9 version using commands from the llvm site. but the compiling error is still there when I use the 'make UE4Editor' command.

The problem is with my ubuntu version? let me know your suggestion.
Thanks a lot for your time and valuable instructions.

---

### Post by Perfect Storm on 2017-05-08
Go to 'Software & Updates' --> make sure everything is checked. Something is missing from your repositories.

EDIT: do at **cat /etc/apt/sources.list**

EDIT: EDIT - what about clang 4.0 does it work for your dependencies? [https://www.ubuntuupdates.org/package/core/zesty/universe/base/clang](https://www.ubuntuupdates.org/package/core/zesty/universe/base/clang)

---

### Post by heaven009 on 2017-05-08
Please take a look and let me know what i'm missing.
[ATTACH=CONFIG]275000[/ATTACH][ATTACH=CONFIG]275001[/ATTACH]

ahd here is the sources.ist file ```
deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu zesty main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu zesty universe main restricted multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu zesty-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu zesty-updates universe restricted main multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu zesty universe
deb http://archive.ubuntu.com/ubuntu zesty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://bd.archive.ubuntu.com/ubuntu/ zesty multiverse
# deb-src http://bd.archive.ubuntu.com/ubuntu/ zesty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu zesty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu zesty-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu zesty partner
deb-src http://archive.canonical.com/ubuntu zesty partner

deb http://archive.ubuntu.com/ubuntu zesty-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu zesty-security universe restricted main multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu zesty-security universe
# deb-src http://security.ubuntu.com/ubuntu zesty-security universe
# deb-src http://security.ubuntu.com/ubuntu zesty-security multiverse
# deb-src http://archive.ubuntu.com/ubuntu zesty main universe restricted multiverse
deb-src http://archive.canonical.com/ubuntu zesty partner
deb http://apt.llvm.org/zesty/ llvm-toolchain-zesty main
deb-src http://apt.llvm.org/zesty/ llvm-toolchain-zesty main
deb http://archive.ubuntu.com/ubuntu zesty-proposed universe main restricted multiverse
```

---

### Post by Perfect Storm on 2017-05-08
It looks alright. I come to think of it, it may that clang 3.6 is not available in ubuntu 17.04. I'm running a ubuntu 16.04 where it's avalable. You could try the link for 3.6:  [http://packages.ubuntu.com/trusty-updates/clang-3.6](http://packages.ubuntu.com/trusty-updates/clang-3.6) (i386 for 32bit amd64 for 64-bit).

---

### Post by heaven009 on 2017-05-08
Yes I already tried them after your first post.
but they fails to install via gdebi. and it opens in software installer but nothing happens when i press install!!
[ATTACH=CONFIG]275002[/ATTACH]
So, do you recommend to use the ubuntu16 lts version? ue4 runs better on the ubuntu 16 version?

---

### Post by Perfect Storm on 2017-05-08
ubuntu 16.04 is well tested and have long support. It's a LTS release so it's recommandable. It's updated every second year.

---

### Post by heaven009 on 2017-05-09
Thanks for your support.
Solved the problem by installing ubuntu16.4,
And this time I didn't use sudo command for everything(this was the main cause of error). 
now using clang3.8.

---

