---
title: "fully updated gutsy?"
date: 2008-02-17
forum: General Help
---

### Post by abcdfv on 2008-02-17
i just installed ubuntu 7.10, and had no internet connection when it installed
now it is telling me that there are no aviailable updates, despite installing from the same disc severla times and having upwards of 180 updates.
i went into update manager and it checked for updates, but still told me there where none avialable.
it is also telling me that the software packet is not aviailable when trying to enable the nvidia restricted driver

---

### Post by FuturePilot on 2008-02-17
When you install offline the installer pretty much comments out your entire sources.list
Try this
System&#8594;Administration&#8594;Software Sources. Check all the boxes in the first tab there. Also uncheck the CD-ROM if it happens to be checked. Go the the Updates tab and check the first two boxes and additionally the fourth to enable the backports. Click Close and then Reload when prompted. Then you should get a bunch of updates as well as the Nvidia driver.

---

### Post by wolfen69 on 2008-02-17
here is a standard gutsy sources list if you need it.

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

---

