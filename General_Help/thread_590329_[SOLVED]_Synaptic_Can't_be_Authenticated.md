---
title: "[SOLVED] Synaptic Can't be Authenticated"
date: 2007-10-24
forum: General Help
---

### Post by Meson on 2007-10-24
All of the packages I'm trying to install say that they can't be authenticated.  However I have not modified my sources.  I use only those that came with 7.10

---

### Post by Maestro23 on 2007-10-24
Can you post your /ect/apt/sources.list

> cat /etc/apt/sources/list

---

### Post by taurus on 2007-10-24
```
cat /etc/apt/sources.list
```
And what happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get safe-upgrade
```

---

### Post by Meson on 2007-10-24
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

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
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```


safe-upgrade is an invalid operation

---

### Post by taurus on 2007-10-24
Try

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Meson on 2007-10-24
update and upgrade work fine.

---

### Post by taurus on 2007-10-24
Try synaptic again and what packages are you trying to install anyway?  You can install them with apt-get.

```
sudo apt-get install <package>
```

---

### Post by Meson on 2007-10-24
Well, I already installed it a while ago, but firestarter.  Then I uninstalled it and went to redo it and I'm gettings these authentications problems.  Another is gvim.  I'm certain these should authenticate.

---

### Post by Meson on 2007-10-24
I reinstalled Synaptic and everything has been resolved.  I'm still curious as to how this problem occured in the first place.

---

### Post by reinfallt on 2007-10-27
I have tried to reinstall both synaptic, apt and dpkg but I still have the same problem. For me it started after I added the GPG key for the medibuntu repository.

---

### Post by Meson on 2007-10-27
Hmm, maybe you should go into your software sources list and hit revert... My Authentication tab has only two entries...

I also did a reinstall of synaptic from within synaptic... hope that helps.

---

