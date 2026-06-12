---
title: "Problem installing generic linux image"
date: 2007-04-11
forum: General Help
---

### Post by VinceDee on 2007-04-11
I'm having problems changing my kernel to SMP in my Dapper. I've tried this:
```
sudo apt-get install linux-image-generic
```

but it only results in an error message:
```
E: Couldn't find package linux-image-generic
```

So I figured it must be my sources.list. I spent the last couple of hours trying various things to update/upgrade and now my sources.list appears to be all nice and clean, but I still get the same error message when trying to fetch that generic kernel.

Just in case it means anything, here's my sources.list:
```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted universe multiverse


deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Am I missing a repository or something?

Vince

---

### Post by anaconda on 2007-04-11
generic kernel comes with edgy.. I dont think you can instal it to Dapper.

Why wont you upgrade to Edgy, (or Feisty)

However if you just want an SMP kernel you can install eg: 2.6.15-28-k7  (if you have AMD processor) and 2.6.15-28-686 for intel processors.

There are several SMP kernels for dapper and you just need to install the correct one..

---

