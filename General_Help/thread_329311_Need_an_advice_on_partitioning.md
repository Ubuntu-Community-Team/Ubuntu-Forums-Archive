---
title: "Need an advice on partitioning"
date: 2007-01-01
forum: General Help
---

### Post by MiCovran on 2007-01-01
I have one hard drive and Windows XP - Ubuntu dual boot. When I first installed Ubuntu, I just wanted to see how it works and thought I'll keep using win mostly. But, as things changed, I'll need more space for my /home partition. This is where I got lost. Here's the output of "sudo fdisk -l": ```
Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        7475    44684797+   f  W95 Ext'd (LBA)
/dev/hda5            1913        4665    22113441    7  HPFS/NTFS
/dev/hda6            4927        4996      562243+  82  Linux swap / Solaris
/dev/hda7            4997        6270    10233373+  83  Linux
/dev/hda8            6271        7475     9679131   83  Linux

```
Now, I know how to shrink hda1 (C: on win) to 1 GB and expand hda2 so it fills the empty space (using gparted), but I don't know **how to move hda5 ( D: ), hda6 (swap), hda7 (/) and hda8 (/home) to the left so I can expand the hda8**, which is on the edge of the disk.

I hope this isn't to confusing.
Any ideas, or I'll have to reformat all from hda5 to 8? :-k 

Thanks.

---

### Post by bruenig on 2007-01-01
You cannot move them to the left without formatting them. The only thing you can do to a partition is either add space to the right or take space away from the right, unless you delete the whole thing and repartition.

---

### Post by kinemagician on 2007-01-01
Be very careful, I was able to delete my entire windows partition.  I strongly suggest to mount Ubuntu on a different Hard-Disk.

---

