---
title: "partial upgrade"
date: 2016-01-22
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-01-22
i seem to have some ppa causing a partial upgrade, how can i figure out which is causing it
an upgrade wants to remove 1/2 my system
im using 14.04
if someone happens see see the issue from what i have:
```
ls  /etc/apt/sources.list.d/
chrome-remote-desktop.list                   stk-daily-trusty.list
chrome-remote-desktop.list.save              stk-daily-trusty.list.save
google-talkplugin.list                       strukturag-libde265-trusty.list
google-talkplugin.list.save                  strukturag-libde265-trusty.list.save
hunter-kaller-ppa-trusty.list                ubuntu-mozilla-security-ppa-trusty.list
hunter-kaller-ppa-trusty.list.save           ubuntu-mozilla-security-ppa-trusty.list.save
kazam-team-unstable-series-trusty.list       webupd8team-atom-trusty.list
kazam-team-unstable-series-trusty.list.save  webupd8team-atom-trusty.list.save
mc3man-fix-test-trusty.list                  xorg-edgers-ppa-trusty.list
mc3man-fix-test-trusty.list.save             xorg-edgers-ppa-trusty.list.save
rolfbensch-sane-git-trusty.list              xubuntu-dev-xfce-4_12-trusty.list
rolfbensch-sane-git-trusty.list.save         xubuntu-dev-xfce-4_12-trusty.list.save
screenlets-ppa-trusty.list                   yorba-ppa-trusty.list
screenlets-ppa-trusty.list.save              yorba-ppa-trusty.list.save
 cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131017)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty main restricted
# deb http://us.archive.ubuntu.com/ubuntu/ trusty main
# deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty universe
deb-src http://archive.ubuntu.com/ubuntu trusty universe
deb http://archive.ubuntu.com/ubuntu trusty-updates universe
deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu trusty multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb http://archive.ubuntu.com/ubuntu trusty-security universe
deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
deb http://archive.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://archive.getdeb.net/ubuntu trusty-getdeb apps games
# deb http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/ /

```

---

### Post by ian-weisser on 2016-01-22
That's quite the Frankensystem you seem to have.

Do not accept a partial upgrade.
Disable each PPA, one at a time. The run apt update. Then try apt upgrade.

When you discover which PPA is the culprit, delete it.

---

### Post by pqwoerituytrueiwoq on 2016-01-22
any idea what would cause a update list download to just hang for a few minutes?
been having this issue all week
i am never doing a partial upgrade after what happened the 1st time
i disabled all sources and it still wants to do a partial

edit: these packages are the problem
gcc-4.9-base gcc-4.9-base:i386 lib32gcc1 libgcc1 libgcc1:i386
```
apt-cache policy gcc-4.9-base gcc-4.9-base:i386 lib32gcc1 libgcc1 libgcc1:i386
gcc-4.9-base:
  Installed: 4.9.2-1ubuntu1
  Candidate: 4.9.3-0ubuntu4
  Version table:
     4.9.3-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 4.9.2-1ubuntu1 0
        100 /var/lib/dpkg/status
     4.9-20140406-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
gcc-4.9-base:i386:
  Installed: 4.9.2-1ubuntu1
  Candidate: 4.9.3-0ubuntu4
  Version table:
     4.9.3-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
 *** 4.9.2-1ubuntu1 0
        100 /var/lib/dpkg/status
     4.9-20140406-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
lib32gcc1:
  Installed: 1:4.9.2-1ubuntu1
  Candidate: 1:4.9.3-0ubuntu4
  Version table:
     1:4.9.3-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 1:4.9.2-1ubuntu1 0
        100 /var/lib/dpkg/status
     1:4.9-20140406-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libgcc1:
  Installed: 1:4.9.2-1ubuntu1
  Candidate: 1:4.9.3-0ubuntu4
  Version table:
     1:4.9.3-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 1:4.9.2-1ubuntu1 0
        100 /var/lib/dpkg/status
     1:4.9-20140406-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libgcc1:i386:
  Installed: 1:4.9.2-1ubuntu1
  Candidate: 1:4.9.3-0ubuntu4
  Version table:
     1:4.9.3-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
 *** 1:4.9.2-1ubuntu1 0
        100 /var/lib/dpkg/status
     1:4.9-20140406-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
```

---

