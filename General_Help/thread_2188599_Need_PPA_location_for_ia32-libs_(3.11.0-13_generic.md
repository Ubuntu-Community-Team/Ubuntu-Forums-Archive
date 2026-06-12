---
title: "Need PPA location for ia32-libs (3.11.0-13 generic)"
date: 2013-11-18
forum: General Help
---

### Post by MsIrey on 2013-11-18
I need ia32-libs installed in order to use gdebi on my 64 bit install.  It doesn't show up in synaptic.  Does anyone know what PPA location I need to add to my repositories?

---

### Post by mc4man on 2013-11-18
gdebi is in the universe repo & has nothing to do with ia32libs

what does this show
```
apt-cache policy gdebi
```

If not there then make sure universe is enabled in software sources or post
```
cat  /etc/apt/sources.list
```

---

### Post by deadflowr on 2013-11-18
What version of Ubuntu are you running??

Here's the package for ia32-libs
[http://packages.ubuntu.com/search?keywords=ia32-libs](http://packages.ubuntu.com/search?keywords=ia32-libs)
and here's launchpad
[https://launchpad.net/ubuntu/+source/ia32-libs](https://launchpad.net/ubuntu/+source/ia32-libs)

Why isn't it simply working for you?
I have gdebi on a 64-bit working just fine, and it doesn't have ia32-libs installed.
(my OS in this case would be saucy)

---

### Post by MsIrey on 2013-11-18
Fresh install of Ubuntu Gnome 3.11.03 generic 64 bit.  Advice I'd been given was that I needed ia32-libs in order to use gdebi on a 64 bit OS and is how I installed on previous version of Ubuntu Unity.  Since I am having other issues that need attention, I thought I'd start with this one which seems the simplest to tackle.  When trying to use gdebi without adding ia32-libs, I get a message that there has been an internal problem.

I need to install my Brother printer drivers on my Aspire 7540-1284.

Result from code apt-cache policy gdebi:
```
gdebi:
  Installed: 0.9.1ubuntu1
  Candidate: 0.9.1ubuntu1
  Version table:
 *** 0.9.1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status
```

Result from code cat  /etc/apt/sources.list
```
#deb cdrom:[Ubuntu-GNOME 13.10 _Saucy Salamander_ - Release amd64 (20131017)]/ saucy main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy universe
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
deb http://security.ubuntu.com/ubuntu saucy-security universe
deb-src http://security.ubuntu.com/ubuntu saucy-security universe
deb http://security.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main

```
Thank you for such speedy replies.

---

