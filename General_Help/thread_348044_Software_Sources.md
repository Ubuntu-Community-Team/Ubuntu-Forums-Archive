---
title: "Software Sources"
date: 2007-01-28
forum: General Help
---

### Post by Graham1 on 2007-01-28
Do I need to add any additional "software sources" to get the latest software and updates?

:)

---

### Post by Ramses de Norre on 2007-01-28
There are sources with restricted packages and such, I'll give you mine but you might want to check whether they are legal in your country before using them.

```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release Candidate i386 (20061017.1)]/ edgy main restricted


#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release Candidate i386 (20061017.1)]/ edgy main restricted

##deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
##deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
#deb http://packages.freecontrib.org/ubuntu/plf edgy-plf free non-free
#deb-src http://packages.freecontrib.org/ubuntu/plf edgy-plf free non-free

## Medibuntu - Ubuntu 6.10 "edgy eft"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free

## wine
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

## Canonical commercial repo
deb http://archive.canonical.com/ubuntu edgy-commercial main
deb http://archive.canonical.com/ubuntu dapper-commercial main

## New amarok
deb http://www.kubuntu.org/packages/amarok-latest edgy main

## Newest binary ati and nvidia drivers (tseliot)
#deb http://albertomilone.com/drivers/edgy/nonlegacy/32bit binary/

## Beryl repo
deb http://ubuntu.beryl-project.org edgy main
```

---

