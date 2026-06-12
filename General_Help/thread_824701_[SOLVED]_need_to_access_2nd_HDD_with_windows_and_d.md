---
title: "[SOLVED] need to access 2nd HDD with windows and data on"
date: 2008-06-10
forum: General Help
---

### Post by directcharitycontribution on 2008-06-10
I have 2nd hard drive with windows and data on > want to view and transfer data then remove drive> hdd detected in gparted (15GB reading as 78GB), not in /etc/fstab > what to do?

fstab as follows
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3b34565e-833c-488d-9a9c-5512fe5fe4d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9a9e3234-47b9-4da2-acc4-5507e13ec172 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


also gparted says setting disk-label will erase drive contents, so no point in that.

---

### Post by HermanAB on 2008-06-10
You need ntfs-3g.  It is in Synaptic.  More info here:
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by directcharitycontribution on 2008-06-10
looking better. and does mounting as windows is necessary to access data files? I say this as I think I have, or had, some kind of mbr issue, and want minimal microsoft sector activity, and the 15GB detected as 78 is making me wary, and there is gluing to do.

is that all it needed?

---

### Post by directcharitycontribution on 2008-06-11
Using ntfs-3g, gets this response.

>  
localhost:~$ sudo mount -t ntfs-3g /dev/sdb /mnt/windows

NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

localhost:~$ sudo mount -t ntfs-3g /dev/sdb1 /mnt/windows
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

localhost:~$ /sbin/mount.ntfs-3g --help
ntfs-3g 1.2216 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2006-2008 Szabolcs Szakacsits
Copyright (C) 2005-2007 Yura Pakhuchiy

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro (read-only mount), force, remove_hiberfile, locale=,
          uid=, gid=, umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

localhost:~$ sudo mount -t ntfs-3g /dev/hdb1 /mnt/windows
ntfs-3g: Failed to access volume '/dev/hdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

localhost:~$ sudo mount -t ntfs-3g /dev/hdb /mnt/windows
ntfs-3g: Failed to access volume '/dev/hdb': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

localhost:~$ sudo ntfs-3g /dev/sdb1 /mnt/win -o force
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type 'ntfs-3g --help' for more information.


---

### Post by directcharitycontribution on 2008-06-11
fdisk gives this output.

> 
localhost:~$ sudo fdisk /dev/sdb

Unable to open /dev/sdb


---

### Post by fooman on 2008-06-11
whats the output of 

```
sudo fdisk -l
```

---

### Post by directcharitycontribution on 2008-06-11
yea just doing that.

---

### Post by directcharitycontribution on 2008-06-11
sudo fdisk -l outputs 

> 
@localhost:~$ sudo fdisk -l

Disk /dev/sda: 15.3 GB, 15303075840 bytes
255 heads, 63 sectors/track, 1860 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1780    14297818+  83  Linux
/dev/sda2            1781        1860      642600    5  Extended
/dev/sda5            1781        1860      642568+  82  Linux swap / Solaris

Disk /dev/sdc: 15.3 GB, 15367921664 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff26ff26

Disk /dev/sdc doesn't contain a valid partition table


so its a 'c drive'!

---

### Post by directcharitycontribution on 2008-06-11
sudo fdisk /dev/sdc, outputs

> 
@localhost:~$ sudo fdisk /dev/sdc
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xcdb29bd4.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 1868.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): ^[[1;2D


---

### Post by directcharitycontribution on 2008-06-11
just installing ntfsprogs and ntfs-config, as well, anyway.
and reading [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

I have 3 (15-40GB) drives to do this to, with some 5 years or so of odd bits of text file, some inventory, so a great motive to get a groove on this.

Then I wil backup online and make a stable set up with a 160GB unit.

---

### Post by MariusSilverwolf on 2008-06-11
> **directcharitycontribution said:**
> sudo fdisk -l outputs 



so its a 'c drive'!

Based on your output, it's an empty drive.  The results "Disk /dev/sdc doesn't contain a valid partition table" indicate there's not an active partition containing data.

---

### Post by directcharitycontribution on 2008-06-11
> **MariusSilverwolf said:**
> Based on your output, it's an empty drive.  The results "Disk /dev/sdc doesn't contain a valid partition table" indicate there's not an active partition containing data.
 but set as a boot drive, it boost windows.

I might try one other drive and see what gives then, but I really would like to extract from this one first.

---

### Post by directcharitycontribution on 2008-06-11
State of play:

fstab as follows seems to have errors. 
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3b34565e-833c-488d-9a9c-5512fe5fe4d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9a9e3234-47b9-4da2-acc4-5507e13ec172 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Should /dev/hda1 and /dev/hda5 be commented out, and no entry for a /dev/hdc/ or /hdb/?

---

### Post by directcharitycontribution on 2008-06-11
> **MariusSilverwolf said:**
> Based on your output, it's an empty drive.  The results "Disk /dev/sdc doesn't contain a valid partition table" indicate there's not an active partition containing data.

So is it possible to make a nominal partition without affecting any other files?

I don't mind if the data comes from an active or inactive partition.

So it looks like I could try using GParted via Super Grub Disk via Setup as a live disk.

---

### Post by directcharitycontribution on 2008-09-16
it, um, sorted itself, after about ten weeks, maybe a bit after a system upgrade.!

---

