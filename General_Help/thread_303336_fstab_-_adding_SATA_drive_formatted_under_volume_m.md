---
title: "fstab - adding SATA drive formatted under volume management"
date: 2006-11-20
forum: General Help
---

### Post by casperl on 2006-11-20
Hi all,
I am busy migrating PC's. I need to migrate data from several hard disks to 1 PC.

The target PC is running Xubuntu Edgy and it boots up from a standard ATA drive addressed as /dev/hda1 etc in /etc/fstab.  This machine is NOT using volume management.  The machine I am setting up the drive on has a SATA interface and is not using SATA drives.   

It turns out that one of the drives (from which data is to be copied) is a serial ATA drive used in a PC running Dapper.  That disk was addressed by Ubuntu using Volume Management and the entry in that disk's fstab was 

> /dev/mapper/Ubuntu-root/ext3 defaults,errors=remount-ro 0 1

Adding this in the target machines /etc/fstab 

> /dev/sda1/data ext3 default 0 2 

does recognise the drive in gparted, but the partition type of the volume cannot be recognised.

adding a /dev/mapper entry () for the SATA drive in the target /etc/fstab does not work either.  This is the entry I tried, and I attempted a couple of variations by substiting the -root part, sans success:

> /dev/mapper/Ubuntu-root/ext3 defaults,errors=remount-ro 0 1

Any suggestions as to how I can get the target PC to recognise the SATA drive for the purposes of copying the data?

Is it simply a question of getting the syntax in fstab right or are additional packages or even a different kernel version required in order to recognise the SATA drive?

TIA

---

