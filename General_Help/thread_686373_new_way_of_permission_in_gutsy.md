---
title: "new way of permission in gutsy"
date: 2008-02-03
forum: General Help
---

### Post by mizar001 on 2008-02-03
I neatly installed an ubuntu gutsy in a friend pc.


It has an ntfs partition, a fat32 partition and the ubuntu partition. Furthermore it has a scanner hp.

The installation was good. All the peripherals detected, and also the scanner, but comparing to feisty the permissions are totally wrong/changed.

In feisty the partitions are automatically loaded in the desktop view, and accessible (fat 32 are also writable). The scanner is completely accessible once connected with Xsane.

In gutsy these are the problems 
-the partitions are visible in 'Computer' window, but to mount them i must digit my superuser password. This is not good, because i run some programs that use some of those directories at startup. 
-once connected the scanner is detected, but the device belongs to root and i can no more get an aquisiotion through xsane as a normal user. This also is not good, because xsane is used by gimp, so i should run gimp/xsane as root to get it working.

Maybe i missed something on a new permissions concepts for gutsy, but can someone drive me in a easy and stable solution ?

---

