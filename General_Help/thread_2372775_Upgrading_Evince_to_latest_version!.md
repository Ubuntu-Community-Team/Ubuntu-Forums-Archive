---
title: "Upgrading Evince to latest version!?"
date: 2017-09-28
forum: General Help
---

### Post by dronts95 on 2017-09-28
Hello everyone,

 I would like to install the latest version of Evince, that has a function I need, but when i tried to do:

```
apt-get upgrade Evince
```

Shell returned that i have already the latest version. I have the 3.14v and the version I would like to have is the 3.22, at least.

The link to the repository is this:

[http://archive.ubuntu.com/ubuntu/pool/main/e/evince/](http://archive.ubuntu.com/ubuntu/pool/main/e/evince/)

However I have the repository with all versions. infact my source.list file content is this:

```
# deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://it.archive.ubuntu.com/ubuntu/ vivid main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ vivid main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ vivid-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ vivid universe
deb-src http://it.archive.ubuntu.com/ubuntu/ vivid universe
deb http://it.archive.ubuntu.com/ubuntu/ vivid-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ vivid-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ vivid multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ vivid multiverse
deb http://it.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ vivid-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu vivid-security main restricted
deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
deb http://security.ubuntu.com/ubuntu vivid-security universe
deb-src http://security.ubuntu.com/ubuntu vivid-security universe
deb http://security.ubuntu.com/ubuntu vivid-security multiverse
deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu vivid partner
deb-src http://archive.canonical.com/ubuntu vivid partner
```

There is the link [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/), which "contain" that I need, so why can' t upgrade Evince?
Moreover i tried to put directly the link of the repository, but i do:

```
sudo apt update
```

It return me the error at the line where I put the link. I put correctly the type (deb) and the component(I tried main and universe).
Can anyone help me? Thank you

---

### Post by QIII on 2017-09-28
Hello!

Vivid has passed its End Of Life and is no longer supported.  It no longer gets software updates.

I would suggest installing a supported version of Ubuntu.  14.04 and 16.04 are the currently supported Long Term Support (LTS) versions, each supported for 5 years beyond their introduction (April 2019 and April 2021, respectively).

As an aside:  just telling us you get an error is not helpful.  It is important to include the full text of the error.

---

### Post by Impavidus on 2017-09-28
As stated, Vivid (15.04) is no longer supported. Trusty (14.04 LTS), Xenial (16.04 LTS) and Zesty (17.04) are supported. Trusty comes with Evince 3.10, Xenial with Evince 3.18 and Zesty with Evince 3.24. After release, every version of Ubuntu stays with the same version of software, except for some important bug fixes and a few exempted applications (like Firefox). **apt-get upgrade** will only install some patches for evince, not a new release. So Xenial will keep Evince 3.18 forever.

The simplest solution for you will be to install Ubuntu 17.04. You'll have to do a fresh install anyway to get from 15.04 to a supported release. 17.04 is only supported until next January, so you'll have to upgrade to 17.10 near the end of this year and then to 18.04 LTS next June or so. First run a live session to make sure it works, and double check your backups are up to date.

Alternatively, you could try to find a PPA or some way to manually install, but that's not recommended.

---

### Post by mc4man on 2017-09-28
What is this feature you're looking for?
(- no particular reason one couldn't use newer evince, use 3.24.1 in 16.04 here

---

