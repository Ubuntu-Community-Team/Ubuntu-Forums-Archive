---
title: "How to mount Solaris partition"
date: 2007-02-01
forum: General Help
---

### Post by Tony Zuse on 2007-02-01
Hi,

how do you mount a Solaris on Edgy? I am new to Linux and used an automated script to mount my Windows partition.

This is my partition table.

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         510     4096543+  1b  Hidden W95 FAT32
/dev/hda2             511        4600    32852925    c  W95 FAT32 (LBA)
/dev/hda3   *        7382       12161    38395350   bf  Solaris
/dev/hda4            4601        7381    22338382+  83  Linux


In /media, there is no hda3 but a supposedly empty hda5...

Thanks.

---

### Post by KeithNoizu on 2007-05-10
I'm running fedora right now and came across the same issue. I'm sure you've figured this out already but i'll post it incase anyone else comes along:


      solaris is a ufs filesystem type sunx86.
      Solaris also creates additional partions that arent necessarily your drive partions or even the same partion numbers you see within solaris.

     So one you have to figure out which partition is which, then you can mount them with the following command.
  
     mount -t ufs -o ro -o ufstype=sunx86 /dev/sde10 /mnt

     sudo that if necessary.

       and replace sde10 and /mnt with appropriate partitions and mount points.

---

### Post by KeithNoizu on 2007-05-10
and be careful, you could kill your solaris partition doing this.

---

