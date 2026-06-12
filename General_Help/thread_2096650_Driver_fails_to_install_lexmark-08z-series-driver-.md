---
title: "Driver fails to install: lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz"
date: 2012-12-20
forum: General Help
---

### Post by pgte3 on 2012-12-20
This package (below) from the Lexmark website fails to install on 12.04 LTS:

lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz

Here is the error, any suggestions on getting this working?

Extracting file: printdriver.te
Extracting file: lexmark-08z-series-driver-1.0-1.i386.deb
Extracting file: launcher.c
Extracting file: launcher
Extracting file: lsbrowser
Extracting file: lsusbdevice
Using dpkg installation
=============================
Execute: dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb > /tmp/selfgz3302/pkg/files/dpkg_msgs

dpkg: error processing lexmark-08z-series-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'lexmark-08z-series-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 lexmark-08z-series-driver-1.0-1.i386.deb
=============================

=============================
Execute: rm lexmark-08z-series-driver-1.0-1.i386.deb

=============================
***** ERROR REPORT *****

---

