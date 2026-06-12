---
title: "[SOLVED] Build-essentials"
date: 2008-03-07
forum: General Help
---

### Post by Fred_E _krugar on 2008-03-07
I cant seem to install build-essential, it keep saying that :

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

so I try to install libc-dev but this is what I get:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5ubuntu2 is to be installed
E: Broken packages

I then try to install g++ and again this is what I get: 

The following packages have unmet dependencies:
  g++: Depends: g++-4.1 (>= 4.1.2-1) but it is not going to be installed
E: Broken packages

What can I do about this??

---

### Post by taurus on 2008-03-07
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Fred_E _krugar on 2008-03-07
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy main restricted
deb-src [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-updates main restricted
deb-src [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy universe
deb-src [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy universe
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-updates universe
deb-src [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy multiverse
deb-src [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy multiverse
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-updates multiverse
deb-src [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-security main restricted
deb-src [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-security main restricted
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-security universe
deb-src [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-security universe
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-security multiverse
deb-src [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
spanky@spanky:~$

---

### Post by Fred_E _krugar on 2008-03-08
So nobody has any ideas??

---

### Post by Fred_E _krugar on 2008-03-08
I had to aptitude to down grade the conflicting packages.

---

