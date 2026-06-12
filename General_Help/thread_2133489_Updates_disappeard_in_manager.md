---
title: "Updates disappeard in manager"
date: 2013-04-08
forum: General Help
---

### Post by ac98521 on 2013-04-08
As far as I can remember there was some recommended updates from my update manager a few days ago. But now they are all gone!!! And whenever I press the check button there are no updates appearing in the manager. What happened and what will I do? Will I still be able to install some good updates from my update manager? Help please

---

### Post by ibjsb4 on 2013-04-08
In terminal enter:

```
sudo apt-get update
```

What happen?

---

### Post by ac98521 on 2013-04-08
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I DID RUN the apt-get update and now it is telling me to run it???

---

### Post by ibjsb4 on 2013-04-08
Try post #4

[http://ubuntuforums.org/showthread.php?t=2133509&p=12594075#post12594075](http://ubuntuforums.org/showthread.php?t=2133509&p=12594075#post12594075)

---

### Post by ac98521 on 2013-04-08
didn't help :((

---

### Post by slickymaster on 2013-04-08
Can you please post the output of:
```
cat /etc/apt/sources.list
```
and:
```
ls /etc/apt/sources.list.d/
```

---

### Post by ac98521 on 2013-04-08
> **slickymaster said:**
> Can you please post the output of:
```
cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository


# libv4l PPA
# deb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu) precise main # disabled on upgrade to precise
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner


and:
```
ls /etc/apt/sources.list.d/
```
cardapio-team-unstable-natty.list.distUpgrade
cardapio-team-unstable-natty.list.save
cardapio-team-unstable-oneiric.list
cardapio-team-unstable-oneiric.list.distUpgrade
cardapio-team-unstable-oneiric.list.save
ferramroberto-java-natty.list.distUpgrade
ferramroberto-java-natty.list.save
ferramroberto-java-oneiric.list
ferramroberto-java-oneiric.list.distUpgrade
ferramroberto-java-oneiric.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
libv4l-ppa-oneiric.list
libv4l-ppa-oneiric.list.distUpgrade
libv4l-ppa-oneiric.list.save
matthaeus123-mrw-gimp-svn-natty.list.distUpgrade
matthaeus123-mrw-gimp-svn-natty.list.save
matthaeus123-mrw-gimp-svn-oneiric.list
matthaeus123-mrw-gimp-svn-oneiric.list.distUpgrade
matthaeus123-mrw-gimp-svn-oneiric.list.save
natty-partner.list
natty-partner.list.distUpgrade
natty-partner.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
scopes-packagers-ppa-precise.list
scopes-packagers-ppa-precise.list.save
steam.list.save
tualatrix-next-oneiric.list
tualatrix-next-oneiric.list.distUpgrade
tualatrix-next-oneiric.list.save
tualatrix-ppa-natty.list.distUpgrade
tualatrix-ppa-natty.list.save
tualatrix-ppa-oneiric.list
tualatrix-ppa-oneiric.list.distUpgrade
tualatrix-ppa-oneiric.list.save
ubuntu-x-swat-x-updates-precise.list
ubuntu-x-swat-x-updates-precise.list.save


Here :)

---

### Post by ibjsb4 on 2013-04-08
Ok, you need to comment out (#) the last two lines in your sources.list

> deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

To look like this

> #deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
#deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

To edit your sources.list open a terminal and enter:

```
gksudo gedit /etc/apt/sources.list
```

Then do another update

---

### Post by ac98521 on 2013-04-08
it still shows 

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by slickymaster on 2013-04-09
After editing your sources.list, commenting ```
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
```, like ibjsb4 said, you didn't forget to save the file, did you?

---

