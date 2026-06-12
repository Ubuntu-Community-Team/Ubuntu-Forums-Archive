---
title: "Unable to write files to UBS stick"
date: 2017-09-04
forum: General Help
---

### Post by satimis on 2017-09-04
Hi all

satimis@PC1B:/tmp&#10219; sudo unzip -cq raspbian_latest.zip > /dev/sdb```

bash: /dev/sdb: Permission denied

```

satimis@PC1B:/tmp&#10219; sudo umount /media/satimis 

satimis@PC1B:/tmp&#10219; sudo unzip -cq raspbian_latest.zip > /dev/sdb```

bash: /dev/sdb: Permission denied

```

satimis@PC1B:/tmp&#10219; unzip -cq raspbian_latest.zip > /dev/sdb```

bash: /dev/sdb: Permission denied

```

&#10219; sudo fdisk -l```

.....
Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 250068991 249067522 118.8G  5 Extended
/dev/sda5       1001472 250068991 249067520 118.8G 8e Linux LVM
....
Disk /dev/sdb: 59.5 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```


Please help.  Thanks

satimis

---

### Post by johndough2 on 2017-09-04
Hi

Perhaps you are trying more steps than you should.

Personally I would check the zip file and extract it to a local folder.

Then look at the file names and extensions.

dd is what I have used in the past to make an SD card for a Raspberry Pi.

The command is effectively a copy structure, with a few extras built in...
```

sudo dd bs=1M if="/home/linux/2013-02-09-wheezy-raspbian.img" of=/dev/mmcblk0

if = INput file   of =  OUTput file  and the mmcblk0 is the usb/sdcard


```


Long version here [https://cmanios.wordpress.com/2013/03/10/install-raspbian-wheezy-linux-to-raspberry-pi-using-linux/](https://cmanios.wordpress.com/2013/03/10/install-raspbian-wheezy-linux-to-raspberry-pi-using-linux/)

---

### Post by satimis on 2017-09-04
> **johndough2 said:**
> Hi

Perhaps you are trying more steps than you should.

Personally I would check the zip file and extract it to a local folder.

Then look at the file names and extensions.

dd is what I have used in the past to make an SD card for a Raspberry Pi.

The command is effectively a copy structure, with a few extras built in...
```

sudo dd bs=1M if="/home/linux/2013-02-09-wheezy-raspbian.img" of=/dev/mmcblk0

if = INput file   of =  OUTput file  and the mmcblk0 is the usb/sdcard


```


Long version here [https://cmanios.wordpress.com/2013/03/10/install-raspbian-wheezy-linux-to-raspberry-pi-using-linux/](https://cmanios.wordpress.com/2013/03/10/install-raspbian-wheezy-linux-to-raspberry-pi-using-linux/)
Hi,

Thanks for your advice.

Before going further copying the extracted files to the SD card, I must sort out how to copy files to the SD card first.  

What file system I must format the SD card?  The factory format of the SD card is exfat.  I format it as ext4

I have tried more than an hour and couldn't figure out the problem.

&#10219; lsblk -f```

NAME   FSTYPE    LABEL UUID                                   MOUNTPOINT
sda                                                           
&#9500;&#9472;sda1 ext2            4b886651-9a08-4d7a-8477-26a078a9c2aa   /boot
&#9500;&#9472;sda2                                                        
&#9492;&#9472;sda5 LVM2_memb       OjlmOV-iMPm-tWnh-DZo9-BSYx-GytX-NxIAKx 
  &#9500;&#9472;ubuntu--vg-root
  &#9474;    ext4            01a2a250-96cc-487c-be2a-780220c7ed82   /
  &#9492;&#9472;ubuntu--vg-swap_1
       swap            51b11fc7-e655-42d3-a1b1-e38312c11c69   [SWAP]
sdb    ext4            348cf5c1-8e6f-41da-af97-7c26bedaaae1   
&#9492;&#9472;sdb1 ext4            3063-6537                              
sr0                                                           
loop0  squashfs                                               /snap/core/1689
loop1  squashfs                                               /snap/inkscape/252
loop2  squashfs                                               /snap/inkscape/188
loop3  squashfs                                               /snap/core/2462
loop4  squashfs                                               /snap/core/1577
loop5  squashfs                                               /snap/inkscape/308

```

I can mount the SD Card but can't copy files to it.

Please help to solve this problem first before going further.

Thanks

Edit
===
Just plugin the SD card to another computer


Warning```

Error mounting /dev/sdd1 at /media/satimis/cc583f6c-0023-4519-9bd9-32940ace9fc4: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdd1" "/media/satimis/cc583f6c-0023-4519-9bd9-32940ace9fc4"' exited with non-zero exit status 32: mount: /dev/sdd1: can't read superblock

```



Regards
satimis

---

### Post by ajgreeny on 2017-09-04
If the sd card, /dev/sdb, is now ext4 you will need to change ownership of its mountpoint to you before you can write to it as user satimis.
```
sudo chown -R satimis:satimis /media/**sd-card**
``` Change **sd-card** to whatever you see in your system.

To make sure that it always mounts at the same address in your filesystem, and that you can recognise it easily, I suggest you give a label to the partition on it which you can do with gparted or with command ```
sudo tune2fs -L labelname /dev/**sdb#**
``` where **sdb#** is the partition which may vary depending on what else is already attached.

---

### Post by satimis on 2017-09-04
> **ajgreeny said:**
> If the sd card, /dev/sdb, is now ext4 you will need to change ownership of its mountpoint to you before you can write to it as user satimis.
```
sudo chown -R satimis:satimis /media/**sd-card**
``` Change **sd-card** to whatever you see in your system.

To make sure that it always mounts at the same address in your filesystem, and that you can recognise it easily, I suggest you give a label to the partition on it which you can do with gparted or with command ```
sudo tune2fs -L labelname /dev/**sdb#**
``` where **sdb#** is the partition which may vary depending on what else is already attached.
Hi,

Thanks for your advice.

This I couldn't resolve.  Just turned off the PC for about 30min

Start the PC

&#10219; sudo fdisk -l
[sudo] password for satimis: ```

Disk /dev/loop0: 141.8 MiB, 148656128 bytes, 290344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop1: 80.5 MiB, 84393984 bytes, 164832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop2: 146 MiB, 153026560 bytes, 298880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop3: 78.4 MiB, 82153472 bytes, 160456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop4: 79.5 MiB, 83349504 bytes, 162792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop5: 142.4 MiB, 149258240 bytes, 291520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xcb5032b9

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 250068991 249067522 118.8G  5 Extended
/dev/sda5       1001472 250068991 249067520 118.8G 8e Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 86.9 GiB, 93243572224 bytes, 182116352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sdb: 59.5 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1  *    32768 124735487 124702720 59.5G  7 HPFS/NTFS/exFAT

Disk /dev/mapper/ubuntu--vg-swap_1: 31.9 GiB, 34254880768 bytes, 66904064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

The file system of /dev/sdb1 change back to HPFS/NTFS/exFAT which is the factory default system, ext4 gone

The icon of SD card is on the left vertical menu.  The SD card is mounted on a card reader.

This is a brand new SD card bought yesterday.

I already did;
$ sudo chown -R satimis:satimis /media/mycard

&#10219; ls -al /media/mycard```

total 8
drwxr-xr-x 2 satimis satimis 4096 Sep  4 20:09 .
drwxr-xr-x 5 root    root    4096 Sep  4 20:09 ..
```

It surprises me.

&#10219; sudo mount -t exfat /dev/sdb1 /media/mycard```

FUSE exfat 1.2.3
ERROR: exFAT file system is not found.

```

exfat-fuse and exfat-utils already installed

&#10219; apt-cache policy exfat-fuse exfat-utils```

exfat-fuse:
  Installed: 1.2.3-1
  Candidate: 1.2.3-1
  Version table:
 *** 1.2.3-1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
exfat-utils:
  Installed: 1.2.3-1
  Candidate: 1.2.3-1
  Version table:
 *** 1.2.3-1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Advice would be appreciated.  I have been struggling for about 3 hours without a solution to mount a SD card

Regards
satimis

---

### Post by satimis on 2017-09-04
Hi all,

Partitioning a SD card

SD card must be partitioned, running "fdisk" and formatting file system before it can be used.  SD card differs from USB drive/stick and can't be treated in the same way as the latter.

Steps:

The SD card is automatically mounted at boot but can't be opened

&#10219; sudo fdisk -l
```

....
Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 250068991 249067522 118.8G  5 Extended
/dev/sda5       1001472 250068991 249067520 118.8G 8e Linux LVM
....
Disk /dev/sdb: 59.5 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 27177C91-C3DF-40E0-85C8-8C38C89A2DD5

Device     Start     End Sectors  Size Type
/dev/sdb1   2048 2050047 2048000 1000M Linux filesystem

Disk /dev/mapper/ubuntu--vg-swap_1: 31.9 GiB, 34254880768 bytes, 66904064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

&#10219; umount /dev/sdb1

&#10219; sudo fdisk /dev/sdb```


Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Command (m for help): d (delete a partition)
Selected partition 1
Partition 1 has been deleted.

Command (m for help): n  (add a new partition)
Partition number (1-128, default 1):  (Enter)
First sector (2048-124735454, default 2048):  (Enter)
Last sector, +sectors or +size{K,M,G,T,P} (2048-124735454, default 124735454): (Enter - using the entire SD card)
Created a new partition 1 of type 'Linux filesystem' and of size 59.5 GiB.

Command (m for help): w (Save & Exit - write table to disk and exit)

```

```

The partition table has been altered.
Calling ioctl() to re-read partition table.
/dev/sdb: close device failed: Remote I/O error
```

Eject the SD card and re-pluggin it

&#10219; sudo mkfs.ext4 /dev/sdb1```

mke2fs 1.42.13 (17-May-2015)
/dev/sdb1 contains a ext4 file system
        last mounted on /media/satimis/9a6d925e-d27a-4290-ab1a-d22fd65d600e on Tue Sep  5 08:30:39 2017
Proceed anyway? (y,n) y
Creating filesystem with 15591675 4k blocks and 3899392 inodes
Filesystem UUID: 16cd5a3b-6180-43db-864e-03abca5477c0
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done  
``` 

Then the SD card is automatically mounted

Right-click SD card icon on the left vertical manuanl -> Open

Still I couldn't drag-n-drop files on the SD card (on its white screen)
&#10219; ls -al /media/mycard/```

ls: cannot access '/media/mycard/.': Permission denied
ls: cannot access '/media/mycard/..': Permission denied
total 0
d????????? ? ? ? ?            ? .
d????????? ? ? ? ?            ? ..

```
What are they ?

&#10219; sudo ls -al /media/mycard/
[sudo] password for satimis: ```

total 8
drw-rw-rw- 2 satimis satimis 4096 Sep  4 20:09 .
drwxr-xr-x 5 root    root    4096 Sep  4 20:09 ..

```

&#10219; ls -l /media/mycard/```

total 0

```

&#10219; ls -ld /media/mycard```

drw-rw-rw- 2 satimis satimis 4096 Sep  4 20:09 /media/mycard

```

&#10219; ls -ald /media/```

drwxr-xr-x 5 root root 4096 Sep  4 20:09 /media/

```

&#10219; sudo chown -R satimis:satimis /media/```

chown: changing ownership of '/media/satimis/16cd5a3b-6180-43db-864e-03abca5477c0/lost+found': Read-only file system
chown: changing ownership of '/media/satimis/16cd5a3b-6180-43db-864e-03abca5477c0': Read-only file system

```

&#10219; ls -l /dev/sdb1```

brw-rw---- 1 root disk 8, 17 Sep  5 09:18 /dev/sdb1

```

&#10219; sudo chown -R satimis:satimis /dev/sdb1

Remove the SD card and Plugin it again.  

Warning popup```

Unable to mount 64 GB Volume
Error mounting /dev/sdb1 at /media/satimis/16cd5a3b-6180-43db-864e-03abca5477c0: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/satimis/16cd5a3b-6180-43db-864e-03abca5477c0"' exited with non-zero exit status 32: mount: /dev/sdb1: can't read superblock
					[OK]

```

Then I can drag-n-drop files on it.

It is very strange to me.

Eject the SD card and reboot PC
&#10219; systemctl reboot

After booting up the icon of SD card is on the left vertical menu.  It is mounted but I couldn't read its content

On terminal:
&#10219; sudo mount -t ext4 /dev/sdb1 /media/mycard
[sudo] password for satimis: ```

mount: /dev/sdb1: can't read superblock

```

&#10219; ls -al /dev/sdb1
brw-rw---- 1 root disk 8, 17 Sep  5 10:01 /dev/sdb1

&#10219; sudo chown -R satimis:satimis /dev/sdb1

&#10219; ls -al /dev/sdb1```

brw-rw---- 1 satimis satimis 8, 17 Sep  5 10:01 /dev/sdb1

```

&#10219; sudo mount -t ext4 /dev/sdb /media/mycard/```

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

&#10219; dmesg | tail```

[ 1042.118456] sd 7:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1042.118465] sd 7:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 1042.118470] sd 7:0:0:0: [sdb] tag#0 Add. Sense: Invalid command operation code
[ 1042.118475] sd 7:0:0:0: [sdb] tag#0 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00
[ 1042.118481] blk_update_request: critical target error, dev sdb, sector 0
[ 1042.118501] JBD2: recovery failed
[ 1042.118509] EXT4-fs (sdb1): error loading journal
[ 1065.433695] usb 3-3: USB disconnect, device number 8
[ 1065.434723] sd 7:0:0:0: [sdb] Synchronizing SCSI cache
[ 1065.434774] sd 7:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK

```

Before I created sdb1 without using the entire SD card.  I can mount it after rebooting the PC.  However I have to go through the complete steps as listed on this posting to make the card works.

I don't know why?

Regards
satimis

---

