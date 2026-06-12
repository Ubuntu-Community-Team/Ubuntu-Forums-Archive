---
title: "Partition blues...."
date: 2007-06-14
forum: General Help
---

### Post by mhenriday on 2007-06-14
After installing **Vista** on a dedicated partiton on my **Windows** disc (I have two 250 GB hard disks on an **AMD 64 X2 5000+** machine, one of which I use for **Windows** - **XP** and now **Vista** - the other for **Feisty**), I found that in order to gain access to **GRUB** when booting the machine, I had to reinstall **Feisty** from my live CD, otherwise I could only access my **Windows** OSs. For various reasons, this process had to be repeated several times, which has resulted in my **Ubuntu** disk (/dev/sdb1) being unnecessarily divided into several partions, as follows (I've attached a screenshot below for the sake of clarity) :
                 
>  Partition                  File system               Mounting point               Size              Used          Unused        Flags
 /dev/sdb1               ext3                           /                                  116.97 GiB     8.44 GiB     108.53 GiB
 /dev/sdb3               ext3                           /media/disk                   20.69 GiB     2.87 GiB       17.82 GiB
 /dev/sdb4               ext3                           /media/disk-1                15.85 GiB     2.75 GiB       13.10 GiB

 /dev/sdb2               extended                                                         79.38 GiB        ---                   ---

     /dev/sdb8            ext3                          /media/disk-2                 62.88 GiB     4.68 GiB     58.21 GiB   boot
     /dev/sdb9            linux-swap                                                         2.72 GiB        ---                   ---
     /dev/sdb7            linux-swap                                                         3.50 GiB        ---                   ---
     /dev/sdb6            linux-swap                                                         4.52 GiB        ---                   ---
     /dev/sdb5            linux-swap                                                         5.75 GiB        ---                   ---

All the ext3's, the extended, and the last linux-swap are marked with a lock as unavailable to the **Gparted editor** in my **Feisty** setup..

What I should like to do is to consolidate all the ext3's and all the linux-swaps to a single division, respectively, leaving /dev/sdb1 as ext3, /dev/sdb2 as extended, and /dev/sdb5 as linux-swap. Any suggestions about how I can go about this ? I presume that I have to download a 64-bits **Gparted editor** to a live CD, as my old 32-bit version won't work, but when this is done, how do I proceed ? This matter is of some importance to me, as, not unexpectedly, I'm having problems with **Vista** and shall probably have to re-install the OS, which means a re-installation of **Feisty** as well. Thus, unless I succeed in mastering manual partitioning, I'm going to find myself, willy-nilly, adding a new and unwanted partion to my **Ubuntu** disk.... 

Henri

---

