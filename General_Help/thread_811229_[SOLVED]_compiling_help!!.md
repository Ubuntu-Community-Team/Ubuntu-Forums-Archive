---
title: "[SOLVED] compiling help!!"
date: 2008-05-28
forum: General Help
---

### Post by cl0ckwork on 2008-05-28
trying to install a plugin for the pidgin messenger client called musictracker.

[URL="http://code.google.com/p/musictracker/"]
http://code.google.com/p/musictracker/[/URL]

i have no idea how to compile/install this into the pidgin directory
can anyone help?

---

### Post by amingv on 2008-05-28
That's in the repos:
```
$ sudo apt-get install pidgin-musictracker
```

For the sake of learning, see here:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
and the file named INSTALL when you extract that package.

---

### Post by cl0ckwork on 2008-05-29
this is what it gives me

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pidgin-musictracker


do i need to add an extra repo?

and i had already tried following the INSTALL file that came with it, but then it tell me it cannot find the pidgin program when i compile it

---

### Post by FuturePilot on 2008-05-29
You probably don't have all the repositories enabled. Can you post the output of
```
cat /etc/apt/sources.list
```

---

### Post by bodhi.zazen on 2008-05-29
See this link to enable your repositories :

[Ubuntu wiki Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by cl0ckwork on 2008-05-29
here is what comes up from  "cat /etc/apt/sources.list"

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse


deb http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb-src http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```

---

### Post by bodhi.zazen on 2008-05-29
pidgin-musictracker is not available in the gutsy repos.


[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pidgin-musictracker&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pidgin-musictracker&searchon=name&subword=1&version=all&release=all)

---

### Post by cl0ckwork on 2008-05-29
thanks thats just what i needed.

it works great.

---

