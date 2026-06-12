---
title: "kmymoney2 dependency problem :("
date: 2007-05-11
forum: General Help
---

### Post by iggyboy on 2007-05-11
I have downloaded the latest kmymoney2 from sourceforge website (I need this for some minor bugs that exit in the repo version) but when ever I run it's show the dependency problem although I have installed those dependency through package manager. Below are the error message:

> 
Selecting previously deselected package kmymoney2.
(Reading database ... 114082 files and directories currently installed.)
Unpacking kmymoney2 (from .../kmymoney2_0.8.6-1_kde3.4.2_i386.deb) ...
dpkg: dependency problems prevent configuration of kmymoney2:
 kmymoney2 depends on kdelibs4 (>= 4:3.4.1-1); however:
  Package kdelibs4 is not installed.
 kmymoney2 depends on libqt3c102-mt (>= 3:3.3.4.3); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing kmymoney2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kmymoney2

I'm not very sure but by guessing; for the missing **kdelibs4** I have install the following package using adept manager: ***kdelibs, kdelibs-data, kdelibs4-dev, kdelibs4c2a.*** For the missing **libqt3c102-mt** I can't find anything that match exact words, however I have install the following packages: ***libqt3-headers, libqt3-i18n, libqt3-java, libqt-jni, libqt3-mt, libqt3-mt-mysql, libqt3-mt-sqlite, libqt3-mt-dev.***

Can someone tell me what did I missed or made wrong, please. Thank you.

---

