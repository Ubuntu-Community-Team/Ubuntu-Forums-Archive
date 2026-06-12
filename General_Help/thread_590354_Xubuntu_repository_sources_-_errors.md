---
title: "Xubuntu repository sources - errors"
date: 2007-10-24
forum: General Help
---

### Post by nicedream on 2007-10-24
Hello, I just installed Xubuntu 7.10 on an old PC I have.  This is a fresh install, not an upgrade.  I was poking around and trying to install a few things, and I noticed that some packaged that are in the unbuntu repositories are not in xubuntu's.

For example, libstdc++5 cannot be found, only version 6. But I have both on my Ubuntu laptop.

Also, I tried to install xawtv for my tuner card in Xubuntu, and it could not resolve one of the dependencies (can't remember which at the moment).  In Ubuntu, this problem does not happen.

So my question is, what gives?  I thought the main diff between the 2 was just the desktop environment, but it seems like a lot of the packages might not exist for Xubuntu.  Or is this because the release just happened last week, and maybe the problems are still being ironed out?

I'm thinking I may just install the Xubuntu desktop packages over an Ubuntu install so that I don't have package problems...

---

### Post by taurus on 2007-10-24
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by nicedream on 2007-10-24
```
root@xubuntu:/home/brian# cat /etc/apt/sources.list
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
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
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
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
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

This file is unchanged since the base  install.  I did try uncommenting the lines that said they "failed to verify", but that made no difference.

---

### Post by nicedream on 2007-10-24
Forgot to mention, the package for "alien" did not install on Xubuntu either.  But it was easily found in Ubuntu.

---

### Post by jpryor68 on 2007-10-24
Uncomment line 7 of your sources.list:

> # Line commented out by installer because it failed to verify: [UNCOMMENT NEXT LINE]
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

That's the pointer to the central repository. You might also comment line 2:

> deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted


That says to first look for files on the installation CD. With that line commented, there would be no difference between what files you see in the repositories and what files any plain Ubuntu user (with the same sources.list) sees.

---

