---
title: "Synaptic error on opening"
date: 2018-08-23
forum: General Help
---

### Post by lumaja2 on 2018-08-23
[SIZE=3]Ubuntu 16.04[/SIZE]
  [SIZE=3]After trying to chance the web sites in Repositories Software & Updates I did something[/SIZE]
  [SIZE=3]wrong and Synaptic opens but shows this error on opening clicking on Close and goes away. [/SIZE] 
 
 
 E: Malformed entry 55 in list file /etc/apt/sources.list (Component)
 E: The list of sources could not be read.
 Go to the repository dialog to correct the problem.
 E: _cache->open() failed, please report.
 
 
 Can someone please help to correct this
 Thank you

---

### Post by Yellow Pasque on 2018-08-23
> E: Malformed entry 55 in list file /etc/apt/sources.list (Component)

Please show the contents of the problematic file:
```
cat /etc/apt/sources.list
```

---

### Post by lumaja2 on 2018-08-24
luis@luis-Ubuntu-16:~$ cat /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release i386 (20160420.1)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
# deb [http://mirror.wiru.co.za/ubuntu/](http://mirror.wiru.co.za/ubuntu/) xenial main restricted
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://mirror.wiru.co.za/ubuntu/](http://mirror.wiru.co.za/ubuntu/) xenial universe
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.saix.net/ubuntu-archive/](http://ubuntu.saix.net/ubuntu-archive/) xenial multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://ubuntu.saix.net/ubuntu-archive/](http://ubuntu.saix.net/ubuntu-archive/) xenial-updates multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://ubuntu.saix.net/ubuntu-archive/](http://ubuntu.saix.net/ubuntu-archive/) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://ubuntu.saix.net/ubuntu-archive/](http://ubuntu.saix.net/ubuntu-archive/) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://ubuntu.saix.net/ubuntu-archive/](http://ubuntu.saix.net/ubuntu-archive/) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse universe restricted main #Added by software-properties
deb [http://ubuntu.saix.net/ubuntu-archive/](http://ubuntu.saix.net/ubuntu-archive/) xenial universe
luis@luis-Ubuntu-16:~$
```

---

### Post by handaxe on 2018-08-26
put a # in front of line 55 in that file, save.  Will need sudo to do the edit.  Error message says something off with that line.

HA

---

### Post by Yellow Pasque on 2018-08-26
Actually, I think the problem might be line 54 because "#Added by software-properties" got added on to the end of that line instead of being put its own line as it should have been.

---

### Post by Yellow Pasque on 2018-08-26
In other words:
```
deb-src http://archive.ubuntu.com/ubuntu xenial multiverse universe restricted main #Added by software-properties
deb http://ubuntu.saix.net/ubuntu-archive/ xenial universe
```
Should be:
```
deb-src http://archive.ubuntu.com/ubuntu xenial multiverse universe restricted main
#Added by software-properties
deb http://ubuntu.saix.net/ubuntu-archive/ xenial universe
```

---

