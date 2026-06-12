---
title: "synaptic - kde-devel missing dependencies"
date: 2008-06-08
forum: General Help
---

### Post by bricedebrignaisplage on 2008-06-08
HI
from synaptic:

kde-devel:
 Depends: kdesdk but it is not going to be installed
 Depends: libarts1-dev but it is not going to be installed
 Depends: kdelibs4-dev but it is not going to be installed
 Depends: kdebase-dev but it is not going to be installed
 Depends: libkonq4-dev but it is not going to be installed


My sources.list:
deb [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) gutsy main restricted multiverse universe
deb [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) gutsy-updates main restricted multiverse universe
deb [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) gutsy-security main restricted multiverse universe
deb-src [http://sg.archive.ubuntu.com/ubuntu](http://sg.archive.ubuntu.com/ubuntu) gutsy-security main restricted multiverse universe


Also in sources.list.d I have a list file with the main repository (same as above without the sg. prefix.)


Where can I find those packages? I checked in [http://packages.ubuntu.com](http://packages.ubuntu.com) and it says that kdesk should be in universe...

Also: Is it a good idea to have several mirrors listed in sources.list.d files? Does it allow to find packages missing in not up to date but faster repositories? And also does it allow to speed up downloading of packages by finding the fastest mirror at that time for that package?

---

