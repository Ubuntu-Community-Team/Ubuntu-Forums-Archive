---
title: "System Monitor won't start anymore"
date: 2008-03-06
forum: General Help
---

### Post by Rafadagaffer on 2008-03-06
Hi, 

I'm aware there have been numerous threads on this problem but all of them seem to be from months ago.

Gnome system monitor will no longer start, it hangs with the error code
```

gnome-system-monitor: symbol lookup error: gnome-system-monitor: undefined symbol: _ZN7pcrecpp6no_argE
```

I'm aware that this was a known bug is Debian a few months back, but google searches have only led me to believe that the problem was fixed.

So can anyone help me out here?

I think it may be a problem with my apt sources list causing the system to update uncessarily.

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ie.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ie.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe

```

Can someone tell me if any  of these sourecs are the cause of the problem or how to rectify it?

Thanks for any help given

PS I suspect I've been an idiot and done this through a fault of my own but please help me out :lolflag:

---

### Post by Mr_Congeniality on 2008-04-13
Having the same issue and I don't get what's going on, someone help!!

---

