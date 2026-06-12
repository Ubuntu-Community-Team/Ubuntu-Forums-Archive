---
title: "Relabeling a hard drive with data already on it"
date: 2016-08-06
forum: General Help
---

### Post by Evil Wayz on 2016-08-06
I recently added two hard drives to my system.  Prior to that I had two hard drives, a Seagate and a western digital.  The Seagate had the OS on it, so the western digital showed up in file manager as 2.0 tb drive.\\Now, the drives I added are the same size and model as second drive.  So I labeled them to keep them straight.  I was wondering if I could relabel the other drive so I can keep them straight.  The reason I ask is when I attempted to do so in gparted, it gave me a warning message to the effect that i could lose data, so i aborted.

I was using this guide, but it was specifically for USB external drives.

---

### Post by Geoffrey_Arndt on 2016-08-06
Need to unmount the drive first, then you can re-label.

---

### Post by CantankRus on 2016-08-07
...or use Disks which allows labelling without unmounting.
Click on the cog wheels of the partition you want to name and choose "Edit Filesystem".

---

### Post by ajgreeny on 2016-08-07
You can also do this in command line with ```
sudo tune2fs -L Labelname /dev/sdx#
``` which is much quicker than using a GUI.

---

