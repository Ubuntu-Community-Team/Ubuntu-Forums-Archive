---
title: "Asterisk package doesn't install"
date: 2005-10-23
forum: General Help
---

### Post by marcw on 2005-10-23
I installed all of the Asterisk dependencies on a fresh Breezy without issue.  But Asterisk itself installs with the following error:

$ sudo apt-get install asterisk
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ohphone kphone asterisk-doc asterisk-dev rate-engine
The following NEW packages will be installed:
  asterisk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1087kB of archives.
After unpacking 3064kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package asterisk.
(Reading database ... 75941 files and directories currently installed.)
Unpacking asterisk (from .../asterisk_1%3a1.0.9.dfsg-1_i386.deb) ...
Setting up asterisk (1.0.9.dfsg-1) ...
adduser: Warning: The home dir you specified already exists.
Adding system user `asterisk'...
Adding new group `asterisk' (114).
Adding new user `asterisk' (114) with group `asterisk'.
Home directory `/var/lib/asterisk' already exists.
adduser: No more than two names.
dpkg: error processing asterisk (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 asterisk
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas?

---

