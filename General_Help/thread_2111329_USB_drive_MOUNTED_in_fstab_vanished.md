---
title: "USB drive MOUNTED in fstab vanished?"
date: 2013-02-01
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-02-01
I have a 4-gig usb thumb drive mounted in fstab as it is has encrypted folders on it. The encryption is Cryptkeeper. The device name is LEXAR.

Last weekend, my entire OS blew up and would not boot. This came after a few days of the boot time issuing a warning about LEXAR could not be mounted. Boot time offered the option of: **S**kip, **M**ount manually. I selected **S**kip. A few more days went by like this and then the OS would not boot.

Here is what info I can supply as of now. Please know that after this problem started, I removed the LEXAR and all the other usb thumb drives.

Also, unfortunately, in attempting repair, during the broken OS time, I pulled the LEXAR while it was in the usb port.

As the various drives have been removed and plugged in again, you may see the drive letter change from /sdb to sdd and the like. It's still LEXAR. I've made very careful to post only the 4-gig LEXAR device info.

I cannot use Cryptkeeper to un-crypt the folder on the thumb drive, copy it elsewhere and re-encrypt it.

Currently, now that the OS is working properly, if LEXAR is plugged in at boot, the OS says SKIP or MOUNT manually. I choose skip. I cannot access the encrypted folder. I have copied that folder to another thumb drive but Cryptkeeper insists on seeing LEXAR for the folder, in order to un-encrypt it.

I NO LONGER want to mount this drive in /etc/fstab. Although I know that it may need that while the problem is fixed. Partly this problem was caused by having Microsoft executables and Linux executables on it. I'm removing the Microsoft partition(s) as soon as this LEXAR problem is resolved and the thumb drive will be reformatted in ext3. Good-bye headaches.

In GRUB Recovery mode, the following appeared on screen. I don't have all of it as the screen scrolled along. Here is what I could copy by hand:

wrong checksum for long filename "Lexar". 
LEXAR\0000\000\000.\[then here is a small diamond shaped icon]\013 non auto-correcting
changed without updating the long name
Lexar short name may have changed without updating the long name
Differences between the Boot Sector and its Backup.
/Lexar [1534] terminated with Status 32 Filesystem is not mounted


**lsusb**

Bus 001 Device 009: ID 05dc:a769 Lexar Media, Inc.

Disk /dev/sdb: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008884e

**cat /etc/fstab**

#Entry for /dev/sdb1 :
UUID=8874-D051	/LEXAR	vfat	##uid=1000,gid=1000,umask=022	0	2

**mark@Lexington-19:~$ sudo blkid**

/dev/sdb1: LABEL="LEXAR" UUID="8874-D051" TYPE="vfat"

**boot-repair-disk said:**

sdc1: ______________________________________

    File system:       vfat
    Boot sector type:  FAT32
    [B]Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.[/B]
    Operating System:  
    Boot files: 

**AND it said:**

Disk /dev/sdc: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     7,700,151     7,700,090   c W95 FAT32 (LBA)

**AND it said:**

Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdc: 3943MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  3942MB  3942MB  primary  fat32        boot, lba

**AND it said:**

df -Th

/dev/sdc1      vfat       3.7G  1.4G  2.4G  37% /mnt/boot-sav/sdc1

**AND it said:**

fdisk -l

/dev/sdc1      vfat       3.7G  1.4G  2.4G  37% /mnt/boot-sav/sdc1

---

### Post by Mark_in_Hollywood on 2013-02-03
Trying stuff at:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Looking over various system-files:

from my etc/fstab

#Entry for /dev/[COLOR="Red"]sdb1[/COLOR] :
UUID=8874-D051  /LEXAR  vfat    ##uid=1000,gid=1000,umask=022   0       2

but 

sudo fdisk -l - sez:

Disk /dev/[COLOR="red"]sdc[/COLOR]: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008884e

Also please note umask=22

not the more typical

umask=000

These two outputs from the terminal are the same 4-gig device. They have gotten very mixed up, viz.: /sdb1 and /sdc1 as same physical device.

What system-files need to change to tell the system that the device is /sdc1 instead of /sdb1 ?

Is this thumb drive not mounting as part of the file-system solved by changing the /etc/fstab to [COLOR="red"]sdc1[/COLOR] - The line starts "#" - so I'm guessing that's not how the OS figures out the fstab entries?

Please see attached screenshot. This device (flash, usb, thumb, pen, jump drive has a Cryptkeeper folder on it. After I had to fix a broken OS, the thumb-drive acts improperly, Cyrptkeeper cannot find it as part of Cryptkeeper stuff.

---

### Post by Mark_in_Hollywood on 2013-02-04
On power up, today, Xubuntu splash screen says /LEXAR not mounted. 
I had pulled the device out during power down last evening. At the splash I saw the usual Skip Mount Manually option. I chose to drop down to root@Lexington-#: and changed the /etc/fstab by removing the ## in that part of the entry concerning /LEXAR. I had never seen those ## before, but they appeared about like this: ##uuid=1000.

I plugged the thumb-drive into the usb port, the OS shows 3 lines about so I guess the device was seen on the usb bus. Next, the OS completed it's boot into the log-in screen and beyond.

BUT, the /LEXAR is not mounted. Or maybe it is, but it doesn't show as part of the file system structure.

So, using the [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

I did the following:

Manually Mounting

Sometimes devices don't automount, in which case you should try to manually mount it. First, you must know what device we are dealing with and what filesystem it is formatted with. Most flash drives are FAT16 or FAT32 and most external hard disks are NTFS.

sudo fdisk -l

Find your device in the list, it is probably something like /dev/sdb1. For more information about filesystems, see LinuxFilesystemsExplained.

Mount the Drive

We can now mount the drive. Let's say the device is /dev/sdb1, the filesystem is FAT16 or FAT32 (like it is for most USB flash drives), and we want to mount it at /media/external (having already created the mount point):

[SIZE="1"]sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137[/SIZE]

The options following the "-o" allow your user to have ownership of the drive, and the masks allow for extra security for file system permissions. If you don't use those extra options you may not be able to read and write the drive with your regular username.

I saw no error returned from the terminal, launched Cryptkeeper and after entering the password, was returned to encrypted folder.

Importantly, how can I remove this device as though it were no longer in the file system and return it to the ordinary status of being a removable device.

---

