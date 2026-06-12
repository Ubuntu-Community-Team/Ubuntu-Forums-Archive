---
title: "could not download all repository indexes"
date: 2008-05-14
forum: General Help
---

### Post by lenspades on 2008-05-14
I am getting could not download all repository indexes when i try to reload Synaptic.Here is my Saved sources list from etc/apt/
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy web universe main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy-updates web universe main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy multiverse
deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy-security web universe main restricted
deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy-security multiverse

---

### Post by plucky on 2008-05-14
First make a copy of your sources list file ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

The edit the file ```
gksudo gedit /etc/apt/sources.list
```

Put a # in front of this line
> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

This stops the update asking for the installation CD to be inserted into the CD drive


Remove the word **web** from these lines > deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy web universe main restricted
deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy-updates web universe main restricted
deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy-security web universe main restricted

I don't think these lines should have the word **web**

Then ```
sudo apt-get update
sudo apt-get upgrade
```


Good Luck

---

### Post by lenspades on 2008-05-14
Work like a charm thanks!! now i am going to upgrade to 8.04

---

