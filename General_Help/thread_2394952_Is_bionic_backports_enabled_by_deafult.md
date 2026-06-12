---
title: "Is bionic backports enabled by deafult ?"
date: 2018-06-24
forum: General Help
---

### Post by linuxyogi on 2018-06-24
[ATTACH=CONFIG]280201[/ATTACH]

Click to enlarge

Is bionic backports enabled by default on a 18.04 install ?

---

### Post by #&amp;thj^% on 2018-06-24
Mine was.
```
# deb cdrom:[Xubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://archive.ubuntu.com/ubuntu bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://archive.ubuntu.com/ubuntu bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
[B]## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
[/B]
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://archive.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://archive.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://archive.ubuntu.com/ubuntu bionic-security multiverse
deb http://archive.ubuntu.com/ubuntu bionic-proposed main multiverse universe restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

---

### Post by linuxyogi on 2018-06-24
@[**[COLOR=#000000]1fallen[/COLOR]**]("https://ubuntuforums.org/member.php?u=2040855")
I dont see backports in your sources. Why is it enabled at my end ? I didnt enable it. Is there any reason to worry ?[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=2040855")

---

### Post by #&amp;thj^% on 2018-06-24
> **linuxyogi said:**
> @[**[COLOR=#000000]1fallen[/COLOR]**]("https://ubuntuforums.org/member.php?u=2040855")
I dont see backports in your sources. Why is it enabled at my end ? I didnt enable it. Is there any reason to worry ?[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=2040855")

It's there:
```
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="#FF0000"]deb http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse[/COLOR]

```
It has been very stable from Development to Release for me.
To me over the 11+ years here in testing>>> the biggest pitfall for some users are adding PPA's without prior knowledge of that PPA and if the maintainer of the PPA keeps it current from release to release.
NOTE: Also worth mentioning having the Proposed Repo enabled can cause some problems.
I hope this helps a bit.:)

---

### Post by linuxyogi on 2018-06-24
> **1fallen said:**
>  NOTE: Also worth mentioning having the Proposed Repo enabled can cause some problems.
I hope this helps a bit.:)

How do I check if the proposed repo is enabled ?

---

### Post by #&amp;thj^% on 2018-06-24
In your picture for Software & Updates>>>The top Tab>>Developer Options
Make sure Proposed is not showing a check mark in the box.

---

### Post by jeremy31 on 2018-06-24
That is under developer options on Software & Updates

---

### Post by linuxyogi on 2018-06-24
> **1fallen said:**
> In your picture for Software & Updates>>>The top Tab>>Developer Options
Make sure Proposed is not showing a check mark in the box.

> **jeremy31 said:**
> That is under developer options on Software & Updates


Found it. Its not enabled. Thanks a lot.

---

