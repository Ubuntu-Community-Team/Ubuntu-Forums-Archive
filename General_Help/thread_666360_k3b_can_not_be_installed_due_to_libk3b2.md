---
title: "k3b can not be installed due to libk3b2"
date: 2008-01-13
forum: General Help
---

### Post by samroaf on 2008-01-13
hello ppl,

i'm trying to install k3b from terminal and from synapatic
each time i try to install it ,it diplay te following output 

 The following packages have unmet dependencies:
  k3b: Depends: libk3b2 but it is not going to be installed
       Depends: libk3b2 (= 1.0.3-1~getdeb1) but it is not going to be installed

when i try to install libk3b2 it display the following 

The following packages have unmet dependencies:
  libk3b2: Depends: libflac++5c2 but it is not installable
           Depends: libflac7 but it is not installable

when i try to install k3b from add remove it display the following 

Cannot install 'k3b'

This application conflicts with other installed software. To install 'k3b' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict

any help well be great full at the moment

---

### Post by taurus on 2008-01-13
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Perhaps you didn't have all the repos available.

---

### Post by samroaf on 2008-01-13
sure here you go


[PHP]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.inode.at/ubuntu/ gutsy main restricted
deb-src http://ubuntu.inode.at/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.inode.at/ubuntu/ gutsy-updates main restricted
deb-src http://ubuntu.inode.at/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ubuntu.inode.at/ubuntu/ gutsy universe
deb-src http://ubuntu.inode.at/ubuntu/ gutsy universe
deb http://ubuntu.inode.at/ubuntu/ gutsy-updates universe
deb-src http://ubuntu.inode.at/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.inode.at/ubuntu/ gutsy multiverse
deb-src http://ubuntu.inode.at/ubuntu/ gutsy multiverse
deb http://ubuntu.inode.at/ubuntu/ gutsy-updates multiverse
deb-src http://ubuntu.inode.at/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sa.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://sa.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://ubuntu.inode.at/ubuntu/ gutsy-security main restricted
deb-src http://ubuntu.inode.at/ubuntu/ gutsy-security main restricted
deb http://ubuntu.inode.at/ubuntu/ gutsy-security universe
deb-src http://ubuntu.inode.at/ubuntu/ gutsy-security universe
deb http://ubuntu.inode.at/ubuntu/ gutsy-security multiverse
deb-src http://ubuntu.inode.at/ubuntu/ gutsy-security multiverse
deb http://ubuntu.org.ua/ getdeb/
[/PHP]

---

### Post by samroaf on 2008-01-13
and up 

^
^
^
^

---

### Post by samroaf on 2008-01-13
^
^
^
^

---

### Post by ramachandren on 2008-02-24
Remove the following line from your sources list and it should work 

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

---

