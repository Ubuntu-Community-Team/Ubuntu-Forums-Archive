---
title: "lack of updates?"
date: 2007-11-24
forum: General Help
---

### Post by skymera on 2007-11-24
whats up with the lack of updates?

ive had hardly any for over a month, probably about 2.

anyone else having near to none?

---

### Post by taurus on 2007-11-24
Do you have those repos enable in /etc/apt/sources.list?  Post it here.

```
cat /etc/apt/sources.list
```

---

### Post by skymera on 2007-11-24
yes i have alll repos, ive used this for almost 8months.
```
 scott@scott-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main universe multiverse #Added by software-properties

deb http://getswiftfox.com/builds/debian unstable non-free

deb http://packages.medibuntu.org/ gutsy free non-free
deb http://dl.google.com/linux/deb/ stable non-free

deb http://debian.space-based.de/debs/ experimental main

deb http://packages.dfreer.org gutsy main
scott@scott-desktop:~$ 

```

---

### Post by mikewhatever on 2007-11-24
You should be getting updates alright. In System>Software Sources, Updates tab, check that Automatic updates are enabled.

---

### Post by taurus on 2007-11-24
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by skymera on 2007-11-24
they all are :S

ive just had hardly any updates.

in fiesty they were daily, now they are barely weekly.

---

