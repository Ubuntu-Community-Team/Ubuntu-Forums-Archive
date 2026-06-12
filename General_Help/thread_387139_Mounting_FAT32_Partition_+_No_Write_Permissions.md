---
title: "Mounting FAT32 Partition + No Write Permissions"
date: 2007-03-17
forum: General Help
---

### Post by DWRZ on 2007-03-17
I created a partition using Partition Magic on Windows XP. Later, I downloaded the GNOME Partition Editor and reformatted the partition. Both times, I used FAT32.

I used the mkdir command to make the following folder: /media/hda4.

My fstab reads:
/dev/hda4 /media/hda4 vfat user,auto

The partition mounts fine. BUT... I have no permissions to write to the folder.

So... :confused:  what gives? How do I fix?

---

### Post by DWRZ on 2007-03-17
Nevermind...fixed! :)

---

### Post by raffytaffy on 2007-03-17
can you tell us how you fixed it..ive been runing into similar problem with external fat32 drive.

---

