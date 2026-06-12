---
title: "Swiftfox repo 403"
date: 2008-03-01
forum: General Help
---

### Post by Sam Lars on 2008-03-01
I'm trying to use the Swiftfox repository using this sources file.
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main
deb http://getswiftfox.com/builds/debian unstable non-free
```

I have been getting this for Swiftfox, though, when apt-get updating
```
Ign http://getswiftfox.com unstable Release.gpg                                           
Ign http://getswiftfox.com unstable/non-free Translation-en_US                            
Ign http://getswiftfox.com unstable Release                         
Ign http://getswiftfox.com unstable/non-free Packages           
Err http://getswiftfox.com unstable/non-free Packages                                      
  403 Forbidden
Failed to fetch http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/Packages.gz  403 Forbidden
```

I've looked quite a bit but I've found almost nothing on this issue.
Could it be related to my using apt-cacher?  I've added it to the server's sources.list, too, but the problem remains.  Wine and Skype seem to update to their repositories fine...

---

### Post by es@urito on 2008-03-02
It looks like a temporary problem in the repository. Ask to the swiftfox team...

---

### Post by es@urito on 2008-03-02
BTW have a look here:
[http://getswiftfox.org/](http://getswiftfox.org/)

---

### Post by Sam Lars on 2008-03-04
Ah, nice, thanks.  I remember now reading that a while ago... I guess I forgot why I stopped using Swiftfox.
So I guess this is solved by not using Swiftfox. :)

---

