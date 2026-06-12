---
title: "open office updates screw up apt-get??"
date: 2007-04-11
forum: General Help
---

### Post by Digitallysick on 2007-04-11
This is what happened after i installed updates, now i cant install, or fix anything

E: Unmet dependencies. Try using -f.
adam@adam-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpthread-stubs0-dev libpthread-stubs0 libxcb-xlib0-dev libxcb1-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openoffice.org-core
The following packages will be upgraded:
  openoffice.org-core
1 upgraded, 0 newly installed, 0 to remove and 84 not upgraded.
12 not fully installed or removed.
Need to get 0B/35.5MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 165409 files and directories currently installed.)
Preparing to replace openoffice.org-core 2.2.0-1ubuntu2 (using .../openoffice.org-core_2.2.0-1ubuntu3_i386.deb) ...
Unpacking replacement openoffice.org-core ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
adam@adam-desktop:~$

---

