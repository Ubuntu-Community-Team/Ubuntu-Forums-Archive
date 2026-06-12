---
title: "Error when running apt-get upgrade"
date: 2007-04-16
forum: General Help
---

### Post by Freddd on 2007-04-16
I get the following error when running the apt-get upgrade command:

> The following packages will be upgraded:
  slocate
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/31.1kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 175520 files and directories currently installed.)
Preparing to replace slocate 3.1-1 (using .../slocate_3.1-1ubuntu0.1_i386.deb) ...
===============================================
===Error. The following diversions still exist:
diversion of /usr/share/man/man1/locate.1.gz to /usr/share/man/man1/locate.notslocate.1.gz by slocate
diversion of /usr/share/man/man1/updatedb.1.gz to /usr/share/man/man1/updatedb.notslocate.1.gz by slocate
===============================================
dpkg: error processing /var/cache/apt/archives/slocate_3.1-1ubuntu0.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/slocate_3.1-1ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Possible to solve :confused:

---

