---
title: "disk boot failure"
date: 2007-11-04
forum: General Help
---

### Post by benner on 2007-11-04
i just installed gutsy in sda1, /home in sda2.  i have 2 more hard drives, hda and sdb.  i have the boot order in the bios set correctly and grub is installed on the correct drive.  nevertheless, when i boot up i get a disk boot failure, insert... error message.  with the live installer i can boot from first hard disk and grub comes up and works without a problem.  any ideas?  i read one other person's post about the same problem but i didn't really understand the solution so i thought i would try asking myself.  thanks in advance for any help.

---

### Post by bingoUV on 2007-11-04
Can you give a link to the other thread, that you think solves your problem too?

Also, give the output of 
```

sudo fdisk -l

```

---

### Post by benner on 2007-11-04
thanks for helping out...

here's the link:
[http://ubuntuforums.org/showthread.php?t=359907](http://ubuntuforums.org/showthread.php?t=359907)

and here's the fdisk -l:


Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e36d3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/hda2            3188        5737    20482875   af  Unknown
/dev/hda3            5738        9627    31246425   83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3315    26627706   83  Linux
/dev/sda2            3316        6630    26627737+  83  Linux
/dev/sda3            6631        6910     2249100   82  Linux swap / Solaris
/dev/sda4            6911       30401   188691457+  83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63ca63ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2481    19923968    7  HPFS/NTFS

---

### Post by bingoUV on 2007-11-04
Your problem is that you cannot boot from /dev/sda1? 

This might be because it is not marked bootable. That is why system can boot from CD, and then choose this partition to proceed, but cannot directly boot from it. See, the * is missing in the fdisk output in /dev/sda1 ?

Use fdisk interactively to mark it bootable. 
```

sudo fdisk /dev/sda

```

Type m for help. p to print current partition table. Notice the lack of a * in /dev/sda1. a to mark a partition active. When it asks you to select a partition, type 1. p again to make sure * has appeared. w to save the  changes.

---

### Post by benner on 2007-11-05
this time i got an error that said 'error loading operating system'.  so i used the live cd to boot from first hard disk again.  (i had tried a similar solution yesterday using gparted and using the manage flags function and selected 'boot' but got this 'error loading operating system' so i went back and unchecked it.  so today, i followed your suggestion and got it again.  any ideas?  thanks so far for your help, bingoUV.

---

