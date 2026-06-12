---
title: "Files still taking up space after repartitioning"
date: 2007-04-11
forum: General Help
---

### Post by rapper97 on 2007-04-11
I had two ext3 partitions, hda3 and hda4. Using Gnome Partition Editor, from the live CD, I got rid of hda4 and expanded hda3 into its place. However, the drive is still being shown as almost completely full, with the space being taken up by the files from hda4, even though neither the files nor the drive, as far as I can tell, exist any longer! How do I let Ubuntu know those files are *gone* and free up space on the disk?

---

### Post by mahy on 2007-04-11
Please post the output of

sudo fdisk -l

---

### Post by rapper97 on 2007-04-11
Probably I should have posted this to "Absolute Beginners"

```
Disk /dev/hda: 40.0 GB 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot   Start    End   Blocks    Id   System
/dev/hda1   *        1    653   5245191    b   W95 FAT32
/dev/hda2          654    784   1052257+  82   Linux swap / Solaris
/dev/hda3          785   4864  32772600   83   Linux
```

---

