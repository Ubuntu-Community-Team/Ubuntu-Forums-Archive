---
title: "Problems with repositories"
date: 2013-06-03
forum: General Help
---

### Post by kokorini on 2013-06-03
Hi all!
Thanks for the help!
when I do sudo apt-get update it throw a lot of connection problems on many repositories.


**like this:**
[...]
W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]



**my soucer.list:**

cacao@Cabrera2:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free # (desactivado en la actualización a maverick)
# deb [ftp://ftp.rediris.es/debian/](ftp://ftp.rediris.es/debian/) unstable main contrib non-free
# deb-src [ftp://ftp.rediris.es/debian/](ftp://ftp.rediris.es/debian/) unstable main non-free contrib
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository

Thanks too you all!

---

### Post by plucky on 2013-06-03
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Natty reached End Of Life six months ago,which means the repositories have been closed.

You should install 12.04 LTS as that is supported until 2017.

Good Luck

---

