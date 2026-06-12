---
title: "not letting me upgrade from feisty to gutsy..."
date: 2007-11-13
forum: General Help
---

### Post by bishop9226 on 2007-11-13
using amd version of feisty...
> 
Failed to fetch [http://wine.lowvoice.nl/apt/dists/gutsy/Release.gpg](http://wine.lowvoice.nl/apt/dists/gutsy/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/gutsy/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/gutsy/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/gutsy/main/binary-amd64/Packages.gz](http://wine.lowvoice.nl/apt/dists/gutsy/main/binary-amd64/Packages.gz) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/binary-amd64/Packages.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/binary-amd64/Packages.gz) 404 Not Found [IP: 195.114.19.35 80]
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz) 404 Not Found [IP: 195.114.19.35 80]


sources.list... i changed all the feistys to gutsys...

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) gutsy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) gutsy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) gutsy main
art@art-desktop:~$ 



---

### Post by Maestro23 on 2007-11-13
**deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) gutsy main**

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

[B]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main
[/B]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END
[B]deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) gutsy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) gutsy main[/B]

All the lines in bold, you need to comment out (#).  Put #'s in front of the deb & deb-src.

Edit the file with gedit, make the changes and save.

> gksudo gedit /etc/apt/sources.list

Then: sudo apt-get update && sudo apt-get upgrade

---

