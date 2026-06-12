---
title: "Please help! I cannot lose this person's data!"
date: 2018-09-11
forum: General Help
---

### Post by YQ002lc2 on 2018-09-11
I was recently forced to boot from an old lubuntu 14.04 live USB when I found myself without a computer.
I could not do what I needed to because everything was so out of date. 
I asked my friend if I could borrow a USB disk. (to make a lubuntu 18.04.1 live USB)
She said that was fine, but please back up her files which she needed for work.
 

I took her flash drive and backed it up to her external HDD. 
I then proceeded to use usb-creator-gtk.
There was some kind of error and it was not allowing me to make the live USB on the flash drive. 
I proceeded to launch gparted to try to reformat the drive before trying again.
I can't remember what gparted said or did. 
It may have gotten hung up or it may have given an error message or it may not have allowed me to do what I needed to with the flash drive I was trying to work on. 

Much to my horror, after using gparted, her external HDD would no longer mount. 
This is my best friend and this is her only hard drive with all her family photos and backed up work files.

Please help! 

The drive is FAT32.
 
I have tried these troubleshooting steps so far: 

1. 
sudo fdisk -l lists the drive:

Disk /dev/sdb: 465.7 GiB, 500074283008 bytes, 976707584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00038a56

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 976707583 976705536 465.7G  7 HPFS/NTFS/exFAT


2. 
sudo fsck /dev/sdb1
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Input/output error while trying to open /dev/sdb1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


3.
sudo e2fsck -c /dev/sdb1
e2fsck 1.44.1 (24-Mar-2018)
e2fsck: Input/output error while trying to open /dev/sdb1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
 
4. 
sudo ntfsfix /dev/sdb1
[sudo] password for user: 
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.

5.
sudo apt-get install chkdsk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package chkdsk

---

### Post by TheFu on 2018-09-11
> Volume is corrupt. You should run **chkdsk**.

That is a Windows program. In general, it it best to use the native OS and disk tools for them for any data corruption or recovery.
And backups are the 2nd and 3rd copies of data, not the only copy.  If that was backup disk, then she should have other copies.

Trying to use NTFS tools on a FAT32 volume is a bad idea too.  Only use the correct tool, for the correct file system if there is corruption.

---

### Post by oldos2er on 2018-09-11
No offense,  but I think it was a mistake for her to give you a flash drive she needed for work.

---

### Post by SeijiSensei on 2018-09-11
e2fsck is meant for ext[234] filesystems that Linux uses natively.  

Can you mount the hard drive from a Windows machine?

---

### Post by oldfred on 2018-09-11
When you have multiple external USB drives, drive order may change. Did you check which was flash drive and which was external backup drive before trying to write image to drive?

Post this:
sudo parted -l

---

