---
title: "Fix for WinXP dual boot problem (? CHS / LBA error)"
date: 2006-11-07
forum: General Help
---

### Post by kharl on 2006-11-07
I am not able to find solution for windows xp dual boot problem. I can boot Ubuntu 6.10 via GRUB menu and it's working fine but windows freeze at the begginning of boot process.

I think there is a problem with CHS/LBA info mismatch in partition table. How to fix it? Please help...

I have tried Super Grub Disk, FIXMBR, GRUB reinstallation. All partitions are OK when I test them with GParted, CHKDSK /p and so on... So I think "start from scratch" is not good solution.

My HDD is (and was) set tu Auto (=> CHS) mode in BIOS. When I change to LBA, the problem persists and in addition GRUB fails to load.

# fdisk /dev/hda
# **************

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylindry of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1008     8096728+   7  HPFS/NTFS
/dev/hda2            1009        2241     9904072+  83  Linux
/dev/hda3            2242        2298      457852+  82  Linux swap / Solaris
/dev/hda4            2299        9729    59689507+   f  W95 Ext'd (LBA)
/dev/hda5            2299        4376    16691503+   b  W95 FAT32
/dev/hda6            4377        9729    42997941    7  HPFS/NTFS

# testdisk
# ********

> TestDisk 6.4, Data Recovery Utility, June 2006
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/hda - 80 GB / 74 GiB - CHS 155061 16 63
Current partition structure:
     Partition                  Start        End    Size in sectors
check_NTFS: Incorrect number of heads/cylinder 255 (NTFS) != 16 (HD)
1 * HPFS - NTFS              0   1  1 16064  15 63   16193457 [System]

Warning: Bad ending head (CHS and LBA don't match)
2 P Linux                16065   0  1 35715  14 63   19808145 [ubuntu]

Warning: Bad ending head (CHS and LBA don't match)
3 P Linux Swap           35715  15  1 36624   5 63     915705

Warning: Bad starting head (CHS and LBA don't match)
4 E extended LBA         36624   6  1 155055  14 63  119379015

Warning: Bad ending head (CHS and LBA don't match)

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

# sfdisk -V /dev/hda 
# ...prints warning about this (sorry I have the message only in Czech :-) )
# so this is a translation:
> Warning: extended disk partiotion doesn't start at the cylinder boundary
DOS and Linux are going to interpret its content differently
Waring: disk partition 2 doesn't end at cylinder boundary.

# SORRY FOR MY ENGLISH ;-)

---

### Post by kharl on 2006-11-08
I am happy to say I found a solution... I wasted a lot of time with  partition checks and corrections but the main problem was somewhere else.

It was the "Windows xp freezes at mup.sys" problem. And the solution was: set ACPI to Enabled in BIOS...

I found a clue at this forum: [http://www.hardwareanalysis.com/content/topic/31874/?o=0](http://www.hardwareanalysis.com/content/topic/31874/?o=0)

---

### Post by ericderace on 2007-10-23
I have pretty much the same problem where my setup is Windows XP and Ubuntu 7.10 on the same hard drive.  
Using Partition Magic 8, i shrunk the windows NTFS partition to make space for Ubuntu.  I then installed Ubuntu on the freed space.
I can boot in both Ubuntu and Windows XP but I wanted to try the VMWare native thing, within Ubuntu.  I could not get it to work, and here's what I found out:
--------------------
TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63, sector size=512

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63
     Partition                  Start        End    Size in sectors
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1  4864 239 63   78155217 [SYSTEM]
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 2 P HPFS - NTFS           4864 240  1 10156  59 63   85004640 [DATA]
 3 P Linux                10157   0  1 12070 254 63   30748410
 4 E extended             12071   0  1 12160 254 63    1445850
 5 L Linux Swap           12071   1  1 12160 254 63    1445787
-------------------

Here's what testdisk tells me.  I believe what happened is that Partition Magic screwed up the partition table, probably from using a different driver when it shrunk the partition.

Now... Both systems work now, I would like to fix that, without deleting the partitions (if possible).  Partition #2 is my data partition, where all my documents is and it's already backed up.

Any help ?

---

