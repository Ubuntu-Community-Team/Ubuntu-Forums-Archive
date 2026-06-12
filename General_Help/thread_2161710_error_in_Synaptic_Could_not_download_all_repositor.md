---
title: "error in Synaptic: Could not download all repository indexes"
date: 2013-07-11
forum: General Help
---

### Post by alimeh on 2013-07-11
when I want to download a package from Synaptic package manager, it show a warning: "NOT AUTHENTICATED" and then can't download it
and when I reload Synaptic, it show this error:
Could not download all repository indexes
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty/InRelease)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty-security/InRelease)  
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/InRelease)  
Failed to fetch [http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu/dists/natty/InRelease)  
Some index files failed to download. They have been ignored, or old ones used instead.

I know that another thread is about this problem in forum ([http://ubuntuforums.org/showthread.php?t=1783872](http://ubuntuforums.org/showthread.php?t=1783872)), but it wasn't helpful for me.
my  /etc/apt/sources.list is:

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)]/ natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

### Post by ajgreeny on 2013-07-11
The old ubuntu natty lost support a while ago so there are no longer any repositories at the old natty url.

[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) may help you, but it is in all honesty better to forget about that and simply install a newer supported version, 12.04. 12.10 or 13.04.

If you don't like unity DE try Xubuntu, Lubuntu or Kubuntu.

---

### Post by alimeh on 2013-07-12
thanks a lot for your reply.
what should I do with that link? ([http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/))
you mean I don't have any solution except installing newer version?
which version has the longest support?

---

### Post by BlinkinCat on 2013-07-12
> **alimeh said:**
> 
which version has longer support?

Ubuntu 12.04.2 has the longest support -

[URL="http://www.ubuntu.com/info/release-end-of-life"]http://www.ubuntu.com/info/release-end-of-life/


[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)



[/URL]

---

