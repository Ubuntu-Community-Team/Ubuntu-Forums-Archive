---
title: "E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)"
date: 2015-08-01
forum: General Help
---

### Post by gangov on 2015-08-01
Hey there, whenever I wanted to add new repository to sources.list, but that didn't end well, so I removed the lines that I added. When I run apt-get update, I got this error:

E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)

I'm using Ubuntu 14.04 LTS and here is how my sources.list file looks like:

```
# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://bg.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://bg.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://bg.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://bg.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://bg.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://bg.archive.ubuntu.com/ubuntu/ trusty universe
deb http://bg.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://bg.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://bg.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://bg.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://bg.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://bg.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://bg.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://bg.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://debian.drdteam.org/ stable multiverse
# deb-src http://debian.drdteam.org/ stable multiverse
deb http://debian.drdteam.org/stable multiverse
# deb-src http://debian.drdteam.org/stable multiverse
```

Can you please tell me what is wrong?

---

### Post by howefield on 2015-08-01
Try changing line 59

```
deb http://debian.drdteam.org/stable multiverse
```

so that there is a space before stable, like this

```
deb http://debian.drdteam.org/ stable multiverse
```

---

### Post by gangov on 2015-08-01
> **howefield said:**
> Try changing line 59

```
deb http://debian.drdteam.org/stable multiverse
```

so that there is a space before stable, like this

```
deb http://debian.drdteam.org/ stable multiverse
```


Thank you so much, that did the job! 

:guitar:

P.S.: You can close the topic.

---

