---
title: "Quad boot destroyed after use of gparted"
date: 2008-05-25
forum: General Help
---

### Post by Raccoon1400 on 2008-05-25
I have an old box quad booting.
on hda, ubuntu gutsy and hardy
on hdb, yoper and slackware

I re-aranged hdb with gparted, moved the slackware partition, and added two new ext3 partitions. I didn't touch hda(this is what I think)

I reboot, and the grub from hdb comes up. This should have been the grub from hda. After I restore grub with super grub disk a couple times, I got hda's grub to appear without fail. However, it took a few tries before I could boot any of the OSs. Now, I can boot hdb's OSs.

When I try to boot either ubuntu on hda, it usually hangs somewhere along the boot process or spits out errors about I/O. hda should not have been touched by gparted. I was lucky enough to get gutsy booted once or twice.

Here's the strange part. When I boot slackware, just before login, it shows the background for xfce I use in hardy or gutsy. I am reasonably sure neither of these images are on the slackware partition.

Should I whipe the whole thing and start again? This is an experimental system, and there is no valuable data. Is there something I can do? Is this the strangest problem ever?

```
bash-3.1# fdisk -l

Disk /dev/hda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1263    10145016   83  Linux
/dev/hda2            1397        2491     8795587+   5  Extended
/dev/hda3            1264        1396     1068322+  83  Linux
/dev/hda5            2388        2491      835348+  82  Linux swap
/dev/hda6            1397        2387     7960144+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         636     5108638+  83  Linux
/dev/hdb2            4864        4998     1084387+  82  Linux swap
/dev/hdb3            1854        4863    24177825    5  Extended
/dev/hdb4             637        1853     9775552+  83  Linux
/dev/hdb5            1854        3430    12667221   83  Linux
/dev/hdb6            3431        4863    11510541   83  Linux

Partition table entries are not in disk order
bash-3.1# 

```

---

### Post by Raccoon1400 on 2008-05-25
gparted doesn't show hda, and cfdisk can't open it.

---

### Post by Raccoon1400 on 2008-05-25
I would whipe the drive if any partition tool could see it.

---

### Post by Raccoon1400 on 2008-05-26
This will put me of gparted for a long time. What do people think of qtparted?

---

