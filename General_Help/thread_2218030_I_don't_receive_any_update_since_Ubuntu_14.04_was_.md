---
title: "I don't receive any update since Ubuntu 14.04 was released"
date: 2014-04-19
forum: General Help
---

### Post by joan_carles2 on 2014-04-19
I was using an alpha version of ubuntu 14.04. I received all the updates and so on but since 14.04 was offiially released I haven't received any update.

Is that normal?

Or maybe I have to do something as change the repositories?

sudo apt-get update + sudo apt-get dust-upgrade doesn't work for me.

My sources.list is next:
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Alpha i386 (20140228)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty main restricted multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty-updates main restricted multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

---

### Post by David D. on 2014-04-19
My experience has been that a few days pass before updates start after a release.  I imagine that the developers are taking a much needed break after the final push for the release.

---

### Post by bapoumba on 2014-04-19
I'm using the main repositories for now, and have received a few updates since release. May be your repos are not up to date, which one es is for ?
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by grahammechanical on 2014-04-19
Your system is on the same repositories that Trusty Tahr has been using since the trusty development cycle begun. Those repositories are the trusty repositories. To put it another way, a fresh install of Ubuntu 14.04 would have the same trusty repositories as your system. Do not expect many updates to 14.04 as development work on it has largely stopped.

Ubuntu 14.04 is now considered a stable release and updates come under the heading of Stable Release Updates. And there are special conditions that have to be met for the update to be allowed.

> [COLOR=#333333][FONT=Ubuntu Beta]Once an Ubuntu release has been completed and published, updates for it are only released under certain circumstances, and must follow a special procedure called a "stable release update" or SRU.[/FONT][/COLOR]

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Here is where we find what Stable Release Updates for Trusty are at present being worked. You will need to scroll down to see Trusty. Remember, this list includes stuff for Ubuntu phone and tablet.

[http://people.canonical.com/~ubuntu-archive/pending-sru.html](http://people.canonical.com/~ubuntu-archive/pending-sru.html)

Ubuntu 14.04 is scheduled for what is called a point release on July 24th. It will then become 14.04.1. So, expect some serious updates at that time.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Regards.

---

