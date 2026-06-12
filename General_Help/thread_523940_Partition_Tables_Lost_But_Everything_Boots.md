---
title: "Partition Tables Lost But Everything Boots"
date: 2007-08-12
forum: General Help
---

### Post by fjgaude on 2007-08-12
I used the partition editor in LiveCD PCLinuxOS 2007 to resize a ext3 partition on a Ubuntu box. That went fine and quick. But, and there is usually "a but", suddenly in Gparted the whole disk is shown to be "unallocated". In horror I rebooted the machine and it did as it always has. This disk has three partitions, each with a version Ubuntu on it, plus, now an unallocated space of about 50Gs, just as I planned. But... fdisk -l shows:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         389     3124611   82  Linux swap / Solaris
/dev/sda2   *         390       11988    93168967+  83  Linux
/dev/sda3           11989       25791   110872534+   5  Extended
/dev/sda4           25792       38913   105402465   83  Linux
/dev/sda5           12487       16569    32796666   83  Linux
/dev/sda6           25246       25791     4385713+  82  Linux swap / Solaris
/dev/sda7           11989       12486     4000122   82  Linux swap / Solaris

Partition table entries are not in disk order
```

My grub has entries in menu.lst for three of the OSs, at sda2, 4 and 5. They each boot correctly. So I'll lost my partition tables but the mbr is correct?

Is there a utility that uses the mbr pointers to create the partition tables so that other programs can see them, like Gparted? Would gptsync do the trick? No, not applicable.

Thanks for the help.

frank

---

### Post by uclalinux on 2007-08-12
you can try


read this
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html)

some programs that might help
gpart
r-cran r-part

---

### Post by fjgaude on 2007-08-12
> **uclalinux said:**
> you can try


read this
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html)

some programs that might help
gpart
r-cran r-part

Thanks, I've seen the HOW-TO before and others like it, but if you understand my issue here, I can boot any and all the various partitions shown by fdisk. This means to me that the partitioner offered in the lastest version of PCLinuxOS has a fault when resizing an ext3 partition. Or maybe just with an extended one as this one is.

It seems that my MBR has the table within it, else grub wouldn't work correctly. There must be a way to rewrite some header on the drive outside of the MBR that programs like Gparted sees, reads to work from, eh?

I have gpart and will see if I can gather enough info to get past this issue. From fdisk I know the START and END positions of the partitions. I'm downing loading r-cran r-part presently.

I'll see how far I can get before I really screw things up. But even then it's not life or death. <smile>

frank

---

