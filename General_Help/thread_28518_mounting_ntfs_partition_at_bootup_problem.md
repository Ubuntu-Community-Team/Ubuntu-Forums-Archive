---
title: "mounting ntfs partition at bootup problem"
date: 2005-04-20
forum: General Help
---

### Post by davegod75 on 2005-04-20
the mount of my windows disk (ntfs partition) is failing at bootup time.
Once I boot up i can mount it just fine.  I also cannot boot to my windows xp drive (sata) unless I change the boot order in the bios thus completely bypassing the linux drive (pata) and grub all together).  Any ideas?

here is my fisk -l results

Disk /dev/hda: 10.2 GB, 10245537792 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1190     9558643+  83  Linux
/dev/hda2            1191        1245      441787+   5  Extended
/dev/hda5            1191        1245      441756   82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       14595    76276620    f  W95 Ext'd (LBA)
/dev/sda5            5100       14595    76276588+   7  HPFS/NTFS


here is my /etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/sda5	/media/windows	ntfs	umask=0222	0	0

---

### Post by shakin on 2005-04-20
I don't know the solution, but you've just described two problems I have on my home machine. Maybe the SATA controller isn't being recognized until too late in the boot process to either boot to it or mount it?

---

### Post by davegod75 on 2005-04-20
[QUOTE=shakin]I don't know the solution, but you've just described two problems I have on my home machine. Maybe the SATA controller isn't being recognized until too late in the boot process to either boot to it or mount it?[/QUOTE]


that's what I was thinking as well..  (i know there are two problems there, but they are  releated and i thought i'd sneak both in here :) )

---

### Post by davegod75 on 2005-04-22
bump...still having this problem

---

