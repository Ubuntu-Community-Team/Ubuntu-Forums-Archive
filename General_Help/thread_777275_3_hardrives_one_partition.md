---
title: "3 hardrives one partition"
date: 2008-05-01
forum: General Help
---

### Post by Pyro_Killer on 2008-05-01
I have an ubuntu which has 4 hdds.
System  80gb 
disk2  160gb
disk3  160gb
disk4  250gb
ext.   200gb

The System disk and ext. (external hdd full of stuff I need) I want to leave untouched. But the the disk's 2-3 I want to combine into a  singel space because it is going to be my fileserver. They are at the moment empty, formatted in ext2. My boot point is in the master boot record. 

Edit: disk2 uses one of those broad cable for data transfer and the 2 others the new slim ones.

---

### Post by Nepherte on 2008-05-01
You can accomplish that with LVM:
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

### Post by elvinatom on 2008-05-01
You can use mdadm software raid and set them up as raid5, that gives you redundancy.
No offense, but if you don't know the difference between SATA and PATA it could be a bit of a challenge. Not that SATA/PATA mattered in your case, but LVM/RAID has to be set up properly since all drives/partitions/filesystems must be configured properly within you OS - if something goes wrong, all data can be lost!

---

