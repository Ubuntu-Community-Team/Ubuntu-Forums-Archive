---
title: "Rename mount partition"
date: 2012-11-04
forum: General Help
---

### Post by evilbrent on 2012-11-04
Hi,

I have a folder **/media/2TB data** that is incorrectly labelled with a space. I try to change it in Nautilus and it says ```
Sorry, could not rename "2TB data" to "sdfsd": Error renaming file: Device or resource busy
```.

Now I think that that this folder is actually the mount point for a partition. GParted says /dev/sdb1 (with label **2TB data**) is "unable to find mount point, unable to read the contents of the file system".

I can actually read and write to this folder just fine, so I don't know what that means.

The output of my fstab is 

> brent@Bertha:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ddce7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      116399   934973943+  83  Linux
/dev/sda2   *      116400      120495    32901120    7  HPFS/NTFS
/dev/sda3          120496      121602     8879105    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5          120496      121602     8879104   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0000b442

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      241742  1941792583+  83  Linux
Partition 1 does not start on a physical sector boundary.

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b7fb47f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1947    15633392    c  W95 FAT32 (LBA)


and I don't see the label **2TB data** anywhere.

My problem is that I need to rename that label, but don't seem to be able to. Can any point me in the right direction?

I'm thinking I need to do this, 

> sudo umount /media/2TB data
sudo rmdir /media/2TB data
sudo mkdir /mnt/2TB

but I'm worried that i'll lose all the data on the drive.

How do I change the label on a mount point without deleting everything and starting again. Any help greatly appreciated.

---

### Post by oldfred on 2012-11-04
Is this a label or a mount point. Nautilus uses labels as an auto-mount point if you are not mounting in fstab. Because of space you have to use quotes or escape the space with the old ASCII code for space. \040

Easy way to label partitions
System> Admin.> Disk Utility

You also can use gparted or command line.
Set Labels for external devices gparted, Disk Utility or command line
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

# to see labels:
ls -l /dev/disk/by-label/
# To clear cache and get new view:
sudo blkid -c /dev/null -o list

When I converted to Ubuntu I gave up on spaces and use under_score, CamelCase, or justonelongstring.

---

### Post by evilbrent on 2012-11-05
Hi, thanks. Changing the label using the disk utility tool seems to have worked - at least as far as viewing the files over the network goes. The partition still isn't mounted right but it seems to work. 

Cheers.

---

