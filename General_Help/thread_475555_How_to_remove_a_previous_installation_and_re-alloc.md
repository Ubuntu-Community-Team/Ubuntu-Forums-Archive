---
title: "How to remove a previous installation and re-allocate space"
date: 2007-06-16
forum: General Help
---

### Post by seoras on 2007-06-16
Hi,
I have a Dell Dimension with 250Gb HDD I partitioned it to 150Gb for WinXP and installed Ubuntu on the other 100Gb. Unfortunately I had problems with the screen resolution and to cut a long story short ended up having to re-install Ubuntu.

The Ubuntu 100Gb partition was named sda4
the first installation went onto sda5
the second installation is on sda7

My problem is that I now want to delete the partition with the first installation (sda5) and re-allocate the space to the good second installation on sda7 but GParted won't let me do this and asks me to un-mount any partitions higher than sda5 first.

Is this at all possible? or is it the case that because the 'good' OS  is on a higher partition (sda7) I cannot delete or format lower partitions (sda5)

Hope that makes sense.

---

### Post by drpaul on 2007-06-16
Any time you mess with partitions you are at risk of messing up the disk.

That said you should boot from a CD/DVD in order to adjust the partitions. From the info you gave it's not clear to me what your problems are. Post the output from "fdisk -l" along with your comments on what you think is where.

HTH

Paul

---

### Post by seoras on 2007-06-16
Here is the output for fdisk -l The fully functioning installation of Ubuntu is on sda7 and the corrupted installation is on sda5. 

I want to delete partitions sda5 and sda6 and re-allocate the disk space to sda7 but cannot seem to be  do this with GParted. I have also tried booting from CD and this too does not allow me to delete/resize/format or do anything else to sda5 and sda6


Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7       11494    92277360    7  HPFS/NTFS
/dev/sda3           30002       30393     3148740   db  CP/M / CTOS / ...
/dev/sda4           11495       30001   148657477+   5  Extended
/dev/sda5           18244       29624    91417851   83  Linux
/dev/sda6           29625       30001     3028221   83  Linux
/dev/sda7   *       11495       17962    51954147   83  Linux
/dev/sda8           17963       18243     2257101   82  Linux swap / Solaris

---

