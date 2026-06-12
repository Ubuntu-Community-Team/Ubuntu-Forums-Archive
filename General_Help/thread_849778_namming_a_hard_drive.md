---
title: "namming a hard drive"
date: 2008-07-04
forum: General Help
---

### Post by jakeiscrazy on 2008-07-04
Hey I recently tired to convert my dad to linux and was wondering if there is a way to rename the hard drive so it is easyer from him to find stuff. So basically I want to change "94.9 GB Media" to "Windows"

---

### Post by unutbu on 2008-07-04
I think what you need to do is change the disk's volume label.
If the disk partition is formated in FAT16, FAT32 or NTFS format, then I think it is necessary to use a Windows program to change the volume label. 

I'm assuming you don't want to lose the data on the partition. If you are willing to reformat it, Linux can set the volume label when it creates a FAT16, FAT32 or NTFS filesystem. It just can't change the label on an existing partition.

---

### Post by sdennie on 2008-07-04
You should be able to change the label on any partition using this guide: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive).  Don't let the name fool you, it works on any type of drive.

---

