---
title: "Bug preventing download of Linux Format 158"
date: 2016-10-27
forum: General Help
---

### Post by resmith2 on 2016-10-27
I purchased Linux Format 158 in the Software Centre. It is not installing. I notice Linux Format 157 - different issue - mentioned in the error log. I think this package may be messed up:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 1649832 files and directories currently installed.)
Preparing to unpack .../lxf158_1.0-0ubuntu2_all.deb ...
Unpacking lxf158 (1.0-0ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/lxf158_1.0-0ubuntu2_all.deb (--unpack):
 trying to overwrite '/opt/futurenet/magazines/data/**lxf157.xpm**', **which is also in package lxf157 1.0-0ubuntu1**
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/lxf158_1.0-0ubuntu2_all.deb
Error in function:
_______________________________________________________________________________________________
I get the error even after deleting: /opt/futurenet/magazines/data/**lxf157.xpm**

---

