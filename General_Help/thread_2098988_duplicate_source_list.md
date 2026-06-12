---
title: "duplicate source list"
date: 2012-12-28
forum: General Help
---

### Post by abelito8 on 2012-12-28
Good morning, I am trying to update through the terminal but it reads

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

...I am running the command asked for...what to do?
I am using Ubuntu 12.04

---

### Post by Cheesemill on 2012-12-28
Can you post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by abelito8 on 2012-12-28
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise universe
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by Cheesemill on 2012-12-28
The duplicate isn't in that file, can you post the output of:
```
ls -l /etc/apt/sources.list.d/
cat /etc/apt/sources.list.d/*
```

Also can you put [noparse]```
 
```[/noparse] tags around your output please, it makes it easier to read.

---

### Post by abelito8 on 2012-12-28
[CODE]
abelito@Ernetsino:~$ ls -l /etc/apt/sources.list.d/
total 48
-rw-r--r-- 1 root root 180 Dec  8 17:02 google-talkplugin.list
-rw-r--r-- 1 root root 174 Nov 17 19:42 gwendal-lebihan-dev-cinnamon-stable-precise.list
-rw-r--r-- 1 root root 174 Nov 17 19:42 gwendal-lebihan-dev-cinnamon-stable-precise.list.save
-rw-r--r-- 1 root root 130 Nov 17 19:42 jconti-gnome3-precise.list
-rw-r--r-- 1 root root 130 Nov 17 19:42 jconti-gnome3-precise.list.save
-rw-r--r-- 1 root root 283 Nov 17 19:42 medibuntu.list
-rw-r--r-- 1 root root 283 Nov 17 19:42 medibuntu.list.save
-rw-r--r-- 1 root root  82 Nov 17 19:42 precise-partner.list
-rw-r--r-- 1 root root  82 Nov 17 19:42 precise-partner.list.save
-rw-r--r-- 1 root root 136 Nov 17 19:42 ubuntuone-stable-precise.list
-rw-r--r-- 1 root root 136 Nov 17 19:42 ubuntuone-stable-precise.list.save
-rw-r--r-- 1 root root 134 Nov 17 19:42 ubuntu-wine-ppa-precise.list

[CODE]


the other one 

[CODE]

abelito@Ernetsino:~$ cat /etc/apt/sources.list.d/*
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
deb http://ppa.launchpad.net/jconti/gnome3/ubuntu precise main
deb-src http://ppa.launchpad.net/jconti/gnome3/ubuntu precise main
deb http://ppa.launchpad.net/jconti/gnome3/ubuntu precise main
deb-src http://ppa.launchpad.net/jconti/gnome3/ubuntu precise main
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
deb-src http://packages.medibuntu.org/ precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
deb-src http://packages.medibuntu.org/ precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
deb http://ppa.launchpad.net/ubuntuone/stable/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntuone/stable/ubuntu precise main
deb http://ppa.launchpad.net/ubuntuone/stable/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntuone/stable/ubuntu precise main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

[CODE]

---

### Post by audiomick on 2012-12-28
Hi. The closing code tags are missing the / . Like this
[noparse] ```
 all your text 
``` [/noparse]

You can use the button marked # at the top of the post window to generate code tags. The one next to it that looks like a  speech balloon makes quote tags, so you get
> a box like this
which is good if you are quoting something from somewhere else.

In that second block of output, nearly all of the entries seem to be doubled. I looked at that on my machine, and mine are all only there once. That could be the problem, but you should wait for someone who knows a bit more about it to tell you what to do about it.

---

### Post by abelito8 on 2012-12-28
ok, thank you Michael, let's hope that someone finds this and knows how to deal with the issue

---

### Post by Toz on 2012-12-28
Precise partner repositories are duplicated in sources.list and in the file /etc/apt/sources.list.d/precise-partner.list. So:
```
sudo rm /etc/apt/sources.list.d/precise-partner.*
```
...then try again:
```
sudo apt-get update
```

---

### Post by abelito8 on 2012-12-28
Thanks a lot, it seems it worked!

---

