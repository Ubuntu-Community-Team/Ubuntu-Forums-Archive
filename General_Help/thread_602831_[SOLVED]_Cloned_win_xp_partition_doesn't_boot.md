---
title: "[SOLVED] Cloned win xp partition doesn't boot"
date: 2007-11-04
forum: General Help
---

### Post by ayampanggang on 2007-11-04
Hello all,

i have a HDD which i want to make a dual boot. In this drive i already have a working ubuntu system, but i want to have windows XP also.

Instead of installing a new OS, I cloned an existing windows XP partition from my older drive into this HDD. So the partition layout in this HDD is now as follows:
/dev/sda1: boot (/boot)
/dev/sda2: swap
/dev/sda3: root (/)
/dev/sda4: the cloned windows XP partition (ntfs)

A note about my cloned windows XP partition: in the MBR i also have a grub installed because i also used to dual boot on my older drive (gentoo and windows).

The problem is, booting the cloned windows partition only gives me "starting up..." message then it just hangs there.

this is the command i used on grub bootloader:
rootnoverify (hd0,3)
makeactive
chainloader +1

additional note: the cloned partition may have a modified MBR, because i used to have windows/linux dual boot on my older drive.

I've looked at another [thread]("http://ubuntuforums.org/showthread.php?t=364409") which suggest a link with solution but it seems the link is dead.

Thank you for your help :)

---

### Post by bingoUV on 2007-11-04
Try making the sda4 partition bootable by following these steps : 
[http://ubuntuforums.org/showthread.php?t=602486](http://ubuntuforums.org/showthread.php?t=602486)

---

### Post by ayampanggang on 2007-11-05
yes it is actually already bootable, heres the actual copy from fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  83  Linux
/dev/sda2               5          66      498015   82  Linux swap / Solaris
/dev/sda3              67       15971   127756912+  83  Linux
/dev/sda4   *       15972       19457    28001295    7  HPFS/NTFS

but still locks at starting up...

i figure maybe i need to reinstall the MBR on the windows partition? or maybe it has got something to do with primary/extended partition

thank you for the reply

---

### Post by bingoUV on 2007-11-05
> **ayampanggang said:**
> yes it is actually already bootable, heres the actual copy from fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  83  Linux
/dev/sda2               5          66      498015   82  Linux swap / Solaris
/dev/sda3              67       15971   127756912+  83  Linux
/dev/sda4   *       15972       19457    28001295    7  HPFS/NTFS

but still locks at starting up...

i figure maybe i need to reinstall the MBR on the windows partition? or maybe it has got something to do with primary/extended partition

thank you for the reply

No, MBR is not for a partition. It is for a hard disk. 

What method did you use to clone a windows partition?

---

### Post by ayampanggang on 2007-11-05
i use low level tool, dd
the command i used:
dd if=/dev/sdb1 of=/dev/sda4
 (sdb1 is the partition in my old drive, sda4 is my new drive)

is there any problem with copying partition of different order (e.g. copying first partition to the fourth partition) as shown with the command above

because in fact, the copied partition is the first partition in my older drive, and i copied it into the fourth partition in my new drive  

thank you for the support so far :)

---

### Post by psusi on 2007-11-05
The windows boot loader is stupid and relies on an exact sector offset from the start of the disk in the boot sector.  This is wrong after cloning the partition, so it can not boot.  Try booting from the windows cd into the recovery console and use the FIXBOOT command, that might fix it.

---

### Post by ayampanggang on 2007-11-06
is that true? that might be the source of problem here.
i'll try to do that with the recovery tool and ill post the result here.

thank you for the support so far :)

---

### Post by bingoUV on 2007-11-06
> **ayampanggang said:**
> i use low level tool, dd
the command i used:
dd if=/dev/sdb1 of=/dev/sda4
 (sdb1 is the partition in my old drive, sda4 is my new drive)

is there any problem with copying partition of different order (e.g. copying first partition to the fourth partition) as shown with the command above

because in fact, the copied partition is the first partition in my older drive, and i copied it into the fourth partition in my new drive  

thank you for the support so far :)

Is the partition size of sdb1 and sdb4 exactly equal? I don't know much about NTFS (only MS does), but it might take offense at being so cloned into dissimilar sized partition. 

If the partition sizes are not exactly equal, you might have to install ntfsprogs and use ntfsresize command. 

Once you fix your partition thus, the FIXBOOT suggestion might work.

---

### Post by ayampanggang on 2007-11-06
no, the size is not exactly equal. the partition in new HDD is larger than the partition in the old HDD but i don't think it is the problem because i can mount and read into the partition successfully. and prior to the cloning, the new partition has been formatted with ntfs first.

i think the fixboot might be a potential solution, ill post what i will come up with after i try it (right now im still at school studying)

thank you

---

### Post by ayampanggang on 2007-11-09
problem solved!

apparently after cloning the whole partition there are some other things i need to do:
1. edit boot.ini file to change the
2. edit the NT boot sector accordingly. this involves inserting some magic numbers e.g. starting bootsector, etc

the full tutorial can be seen here:
[http://m.domaindlx.com/LinuxHelp/win/copyingXP.htm](http://m.domaindlx.com/LinuxHelp/win/copyingXP.htm)

thank you so much you guys have been helpful :)

---

