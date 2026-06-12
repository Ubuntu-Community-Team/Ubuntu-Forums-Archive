---
title: "Using LVM in 18.04.1"
date: 2018-11-02
forum: General Help
---

### Post by john186 on 2018-11-02
I am trying to perform a fresh install of 18.04.1.  I have 3 500GB disks and at first I tried to combine them in the manual configuration into one VG (rootvg) but I could not create a /BOOT LV as it was greyed out.  I have also tried to install on a single disk also in manual mode setting up a VG then creating Logical Volumes for root and swap but again boot is greyed out!  I do not want to use the automatic LVM manager as I wish to be in control of the names of the VG etc.  Also the DONE button is greyed out so cannot complete the disk partitioning.

Help please.

---

### Post by john186 on 2018-11-02
I solved it by doing a bit of digging around the local disks.  I found /boot has to be a separate partition on a local disk.

---

