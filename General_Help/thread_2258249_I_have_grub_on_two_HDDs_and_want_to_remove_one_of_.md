---
title: "I have grub on two HDDs and want to remove one of them"
date: 2014-12-26
forum: General Help
---

### Post by andrei11 on 2014-12-26
The Linux install is Ubuntu Gnome 14.04 LTS, with Gnome 3.0   I think (the stable one)
My setup is:  3 HDD
in the bios order and also what Disks report:

2 TB hard drive (full ext4 (/home) with grub at the MBR, this is the one I want to keep)
750 GB hard drive with (full NTFS partition, the grub from the failed attempt, rather was not supposed to install here grub, but messed up the letters of devices when I installed Ubuntu gnome the first time) - this is the grub I want to remove.
1 TB hard drive with no grub, but win 7 (2 ntfs partitions, and at the end of drive a extended partition witch contanins linux swap and root / partition)

The options of boot are in this order above, meaning that it boots "sometimes not at all or extremely slowly(grub menu does not show up) sometimes it just goes directly to linux" if I tell it from the quick boot in bios F12 to go in the 2 TB hard drive does not boot at all.

What I want is to remove the grub from the 750 GB hard drive and possibly get advice on why is grub acting so strange.

Maybe I should remove both of grub installs and reinstall but I don't know how to do that. There should be a way from within Linux installation isn't ?? Please help.

---

### Post by hal8000b on 2014-12-26
You need to state the linux drive designations, however post the output of this command with your next post:

sudo fdisk -l

This will list all partitions with designations and brief drive sizes so it can be worked out.
As one drive is 2TB you may well be using mixed GUID and Intel MBR partition tables.

I have 2 hard drive (both 500G so my partition table is MBR) and I have grub on one drive and burg on another.
The BIOS boot order determines which drive I boot from and whether I want to use burg or grub.

If grub is only on one drive and you mess things up, then recovery is only possible via a live CD/DVD or USB drive.
The advantage (for me) have having 2 bootloaders is that if I mess one up I change the BIOS sequence.

Having grub on multiple drives should not make things slow.  The fact that grub is appearing slowly may be
some other issue or some configuration issue.

I would not remove the grub installs as yet, as grub can only boot from one drive at a time, post the output from
fdisk and also if you created GUID partition table.

If you are unsure about GUID  or partion then you can use command

sudo fdisk /dev/sda

You will need to replace sda with sdb and sdc but if any drive has a GUID partition table the
output will look like below:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   312581807   156290903+  ee  GPT


Also did you install grub in a partition or in the mbr of each drive?

---

### Post by andrei11 on 2014-12-27
Linux installation sais just that install on /dev/sda, not sda1 ---- I asume that would be mbr and not first (only 1) partition
2 tB is GPT I know this because that's how I formated in windows, the other is mbr
I've reinstalled Ubuntu and the problem seems to have gone away though. So I don't think it's a problem anymore, I;ve always put grub on the gpt 2tb drive and so far it;s the first time I had any problems. Right know I'm kind of distro hopping and will install as of this posting, Linux Mint mate 17 64bit, hope I dont get the slowdown like in Cinnamon version 17.1 Although cinnamon seems to be more feature rich. I';m hoping also that 17 is more bug free than 17.1, the partitions will be the same, grub on the gpt 2tb drive.

There's is one more detail:  since I first made the 2tb drive ntfs gpt, after I made several installations of linux meaning using this for a 2tb /home partition I selected new partition table. doesnt that delete the gpt filesystem and make it mbr ? I;m not sure...

this is what fdisk prints out
Command (m for help): v   
Remaining 4206 unallocated 512-byte sectors

Command (m for help): p   

Disk /dev/sda: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005218

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3907024895  1953511424   83  Linux

---

### Post by oldfred on 2014-12-27
For grub to correctly install on gpt partitioned drives for BIOS boot, you must have a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive. You can use gparted to shink any partition a tiny amount and create the bios_grub partition. Not required for MBR(msdos) partitioned drives.

May be best to see all details of installs.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

