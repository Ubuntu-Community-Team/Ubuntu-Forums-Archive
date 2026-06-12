---
title: "libc6 (&gt;= 2.3.2.ds1-21) missing!"
date: 2005-09-28
forum: General Help
---

### Post by arlie on 2005-09-28
I did this

sudo dpkg -i libchix_1.0.0-1_i386.deb 

and got this

Selecting previously deselected package libchix.
(Reading database ... 96754 files and directories currently installed.)
Unpacking libchix (from libchix_1.0.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of libchix:
 libchix depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
dpkg: error processing libchix (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libchix
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How do I get the missing packages?

---

### Post by Zotova on 2005-09-28
Hi, I've put the file you are missing on my server for you.

In terminal type:

wget [http://www.shanghai.me.uk/linux/libc6_2.3.5-6_i386.deb](http://www.shanghai.me.uk/linux/libc6_2.3.5-6_i386.deb)

Then use the usual dpkg

dpkg -i libc6_2.3.5-6_i386.deb

That should hopefully fix your dependancy issues.

---

### Post by arlie on 2005-09-28
did this

sudo dpkg -i libc6_2.3.5-6_i386.deb
Password:

got this

dpkg: regarding libc6_2.3.5-6_i386.deb.1 containing libc6:
 libc6 conflicts with initrd-tools (<< 0.1.79)
  initrd-tools (version 0.1.77ubuntu3) is installed.
dpkg: error processing libc6_2.3.5-6_i386.deb (--install):
 conflicting packages - not installing libc6
Errors were encountered while processing:
 libc6_2.3.5-6_i386.deb

---

