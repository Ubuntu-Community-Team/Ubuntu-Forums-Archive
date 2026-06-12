---
title: "Where is acroread, mozilla-acroread, and acroread-plugins?"
date: 2007-02-08
forum: General Help
---

### Post by Red Knuckles on 2007-02-08
In the Unofficial Ubuntu Starters Guide it says that to install acroread, and mozilla-acroread you:

sudo aptitude install acroread mozilla-acroread acroread-plugins

when I do I get:

$ sudo aptitude install acroread mozilla-acroread acroread-plugins
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "acroread"
Couldn't find any package whose name or description matched "mozilla-acroread"
Couldn't find any package whose name or description matched "acroread-plugins"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Am I missing a repo. I'm in Kubuntu Feisty Fawn Herd 3. My '/etc/apt/sources.list':

# 
# deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Alpha i386 (20070201.1)]/ feisty main restricted

# deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Alpha i386 (20070201.1)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted  universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free


## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

Or do I have to install from tar ball? :confused: This was in repos in Edgy>Breezy.

---

### Post by tbroderick on 2007-02-08
I don't think it's available as a Feisty package right now. That's the trouble with using a testing distro, but you can install the Edgy version. That should work. Go to packages.ubuntu.com and search for acroread in the Edgy repo. You can download the .deb by clicking on the matching architecture.

---

### Post by altonbr on 2007-02-08
I thought you could only install those through Automatix (or whatever repositories Automatix uses).

---

### Post by Red Knuckles on 2007-02-08
> **tbroderick said:**
> I don't think it's available as a Feisty package right now. That's the trouble with using a testing distro, but you can install the Edgy version. That should work. Go to packages.ubuntu.com and search for acroread in the Edgy repo. You can download the .deb by clicking on the matching architecture.

Thanks.:)  I should have known that but I guess I just forgot or had brain lock. I guess one could find most any package from older versions and be OK. 
:lolflag:

---

