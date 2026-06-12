---
title: "Error Formatting Drives"
date: 2007-10-13
forum: General Help
---

### Post by RaygionsSumta on 2007-10-13
I am running Feisty Fawn Server on an EPIA 5000 mini-itx motherboard, and attempting to add a 4 (400MB) disk software RAID-5 to the system.  The 4 disk drives are attached to the system via a Promise SATA300 TX4.
The trouble is that I am unable to format my drives and the listed causes of the issue do not seem to be applicable.
```

~$ sudo mkfs.ext3 /dev/sda1
mke2fs 1.40-WIP (14-Nov-2006)
/dev/sda1 is apparently in use by the system; will not make a filesystem here!

```

Everything that I google suggests that the reason for this error is that a partition on the drive is already mounted.  As each of the SATA drives has only one partition, the one I am attemping to format, it seems unlikely.  I did try 
```
sudo umount /dev/sda1
umount: /dev/sda1: not mounted

```.

One other datapoint is the error i get partitioning.  It does not seem to prevent the partition from being created, but still...

```
WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
```
~$ sudo fdisk /dev/sda
```

The number of cylinders for this disk is set to 48641.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-48641, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-48641, default 48641): 
Using default value 48641

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```
~$ sudo fdisk -l
```

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4632    37206508+  83  Linux
/dev/hda2            4633        4870     1911735   82  Linux swap / Solaris

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801   fd  Linux raid autodetect


```

---

### Post by louieb on 2007-10-13
If you were running a desktop I'd suggest you go to system>preferences> removable media and uncheck all the auto mount boxes. Theres a bug or feature where Ubuntu will auto mount a partition when its accessed by a partition program.

I guess use a live cd either GParted or System Rescue to format your drives.

---

### Post by fjgaude on 2007-10-14
Software raid using mdadm? or dmraid?

On the Promise controller, are the drives declared as JBODs, or Linear?

---

### Post by RaygionsSumta on 2007-10-14
> Software raid using mdadm? or dmraid?

On the Promise controller, are the drives declared as JBODs, or Linear?

Eventually I will use mdadm, but I first I have to get the drives formatted.  
The Promise controller is not a RAID controller.  Just a SATA II controller card.

---

### Post by fjgaude on 2007-10-15
I remember having this same problem awhile back. Try using cfdisk to format the disks.

```
sudo cfdisk /dev/sda1
```

The disk may not have the initial MBR on them, or something like that.

---

