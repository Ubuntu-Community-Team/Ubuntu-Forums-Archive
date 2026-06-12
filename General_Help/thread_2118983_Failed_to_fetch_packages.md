---
title: "Failed to fetch packages"
date: 2013-02-22
forum: General Help
---

### Post by MtnDew on 2013-02-22
I keep getting this error when I run "**sudo apt-get update && apt-get upgrade**".

> W: Failed to fetch [http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
I have checked /etc/apt/sources.list and the software sources list, there is no package by that or a similar name. How do I remove or fix this package? 

Ubuntu 12.10

---

### Post by dgharmon on 2013-02-22
> **MtnDew said:**
> I keep getting this error when I run "**sudo apt-get update && apt-get upgrade**".

You've added a package that don't exist, you need to remove it from /etc/apt/sources.list

---

### Post by MtnDew on 2013-02-22
> **dgharmon said:**
> You've added a package that don't exist, you need to remove it from /etc/apt/sources.list

As I mentioned previously, there is nothing in my /etc/apt/sources.list that contains the same link or description. 

```

# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted
# deb http://packages.linuxmint.com/ quantal main upstream import
deb http://archive.ubuntu.com/ubuntu quantal main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu quantal-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ quantal partner
deb http://packages.medibuntu.org/ quantal free non-free

deb http://archive.getdeb.net/ubuntu quantal-getdeb apps
deb http://archive.getdeb.net/ubuntu quantal-getdeb games

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu quantal restricted
deb-src http://archive.ubuntu.com/ubuntu quantal main restricted


## Spotify: 
deb http://repository.spotify.com stable non-free
##
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu quantal-updates restricted
deb-src http://archive.ubuntu.com/ubuntu quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb-src http://archive.ubuntu.com/ubuntu quantal universe
deb-src http://archive.ubuntu.com/ubuntu quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb-src http://archive.ubuntu.com/ubuntu quantal multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://archive.ubuntu.com/ubuntu quantal-security main restricted
deb http://archive.ubuntu.com/ubuntu quantal-security universe
deb-src http://archive.ubuntu.com/ubuntu quantal-security universe
deb http://archive.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
deb http://archive.ubuntu.com/ubuntu quantal-backports restricted main multiverse universe

```

---

### Post by plucky on 2013-02-22
PPA's are located in /etc/apt/sources.list.d ```
ls /etc/apt/sources.list.d/
``` and remove it from there.


Good Luck

---

### Post by grahammechanical on 2013-02-22
Can you confirm that you have opened System Settings>Software Sources (may also be called Software & Updates)> Other Software tab and made sure this PPa is not listed there.

Regards.

---

