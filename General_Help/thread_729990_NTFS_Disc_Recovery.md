---
title: "NTFS Disc Recovery"
date: 2008-03-20
forum: General Help
---

### Post by gloken on 2008-03-20
To cut to the chase, I have a hard drive I'm trying to collect some data from.
I was able to mount it as dev/hdb and ran ddr_rhelp to recover the data to /media/disk/backup.img (on my external drive)

>sudo fsck -y /media/disk/backup.img

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

>sudo e2fsck -b 8193 /media/disk/backup.img

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Some reading informed me that this is because fsck apparently doesn't work with NTFS file structure.

>sudo mount -t ntfs -o force,loop /media/disk/backup.img /mnt/recovered

NTFS signature is missing.
Failed to mount '/dev/loop7': Invalid argument
The device '/dev/loop7' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

>sudo fdisk -l /dev/hdb

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeeebeeeb

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9964    80035798+   7  HPFS/NTFS

Does anyone know what I'm doing wrong, and if there is any way I can mount this image to get at any usable data that's left on the old drive?  Any help would be much appreciated, I'm running out of ideas.

---

### Post by az on 2008-03-20
See [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) and the ubuntu-rescue-remix website.

Were you able to image the whole drive without errors?

Did you image the entire disk or just the NTFS partition?

If so, use 

mmls utility from The Sleuth Kit to see the partition table on the image file.  Then mount the loop filesystem using the offset option.

For example, and NTFS partition is usually 63 blocks from the beginning of the drive.  One block is 512 bytes (63*512=32256)

sudo mount -o loop,offset=32256 file mnt

---

### Post by gloken on 2008-03-20
First off, thanks for the help.  I did image the drive without any errors.  I've never had to do this before and am very new to ubuntu, but I'm digging through man pages and trying to keep ahead of the game. 
I believe it imaged the entire drive.

>mmls /media/disk/backup.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Description
00:  -----   0000000000   0000000000   0000000001   Primary Table (#0)
01:  -----   0000000001   0000000062   0000000062   Unallocated
02:  00:00   0000000063   0160071659   0160071597   NTFS (0x07)



>sudo mount -o loop,offset=32256 /media/disk/backup.img /mnt/restored

Failed to read last sector (160071596): Invalid argument
Perhaps the volume is a RAID/LDM but it wasn't setup yet, or the
wrong device was used, or the partition table is incorrect.
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?



>fdisk -lu /media/disk/backup.img
You must set cylinders.
You can do this from the extra functions menu.

Disk /media/disk/backup.img: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeeebeeeb

                 Device Boot      Start         End      Blocks   Id  System
/media/disk/backup.img1   *          63   160071659    80035798+   7  HPFS/NTFS
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(9963, 254, 63)

Does this mean that my partition table is corrupt?

---

### Post by will103 on 2008-03-21
The partition table might be corrupted.

Download the live CD 'recovery is possible' (Google it). Boot from the CD and use the TestDisk app (from the terminal). This will scan the disk for file systems (ignoring the current MBR). If you cannot 'see' your partition then do a deep search. The instructions for this are a bit sparse but try looking at:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

This app has saved me in the past.

will103

---

### Post by az on 2008-03-21
> **gloken said:**
> 
>sudo mount -o loop,offset=32256 /media/disk/backup.img /mnt/restored

Failed to read last sector (160071596): Invalid argument

Does this mean that my partition table is corrupt?

Probably.

> **will103 said:**
> 
Download the live CD 'recovery is possible' (Google it). Boot from the CD and use the TestDisk app (from the terminal). This will scan the disk for file systems (ignoring the current MBR). If you cannot 'see' your partition then do a deep search. The instructions for this are a bit sparse but try looking at:


First off, you can use testdisk from your own ubuntu install.  

sudo apt-get install testdisk

Second, if you want a live cd for data recovery, ubuntu-rescue-remix is more current than RIP.

Also, testdisk is not the right tool.  The problem is not that the parition is missing, it's right there.

The problem is that the filesystem on the partition appears to be damaged.  The testdisk package also provides photorec which is a file carver.  When you don't have a working filesystem, file-carving is how you get your files back.

Another excellent file carver is foremost.  It too is available on the ubuntu-rescue-remix live USB or CD.  You can also just apt-get install it.

---

### Post by gloken on 2008-03-22
The file system does seem to have been damaged, but I ran Foremost and recovered a fraction of the data. 

I lost most of the data, but retrieved some irreplaceable pictures, so that's something at least.
Thanks a lot for all the help. I think I'll learn to back up my files in the future.

---

