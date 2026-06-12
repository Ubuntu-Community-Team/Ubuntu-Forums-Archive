---
title: "SD card not recognized"
date: 2015-12-08
forum: General Help
---

### Post by s9032g@comcast.net on 2015-12-08
I just noticed that my SDHC 8 GB card is not being recognized. Until I switched from Ubuntu to Xubuntu 14.04 it was recognized and used for extra memory. I see some exotic ideas on line that I hesitate to try.

The SD card is always in the slot so it is in when I boot up.

---

### Post by sudodus on 2015-12-08
Please check if the SD card is recognized at all: run the following commands and post the result in a reply,

```
lsusb

sudo parted -ls

sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
```

It should be recognized as a mass storage device, /dev/sdx, where x is the drive letter. In that case you should be able to mount it, even if it is no longer auto-mounted.

- What happens if you unplug and re-plug the SD card? (Do this only when the partitions on the card are ***not*** mounted.)

---

### Post by s9032g@comcast.net on 2015-12-08
Yes. Thank you. I have done all that prior to posting the thread.

Zero recognition. The SD card is recognized by, for example, my camera (test)

---

### Post by s9032g@comcast.net on 2015-12-08
Model: ATA STEC PATA 16GB (scsi)
Disk /dev/sda: 15.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.3GB  14.3GB  primary   ext4            boot
 2      14.3GB  15.4GB  1062MB  extended
 5      14.3GB  15.4GB  1062MB  logical   linux-swap(v1)


steven@steven-Inspiron-910:~$ sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
MODEL            NAME   FSTYPE LABEL MOUNTPOINT   SIZE
STEC PATA 16GB   sda                             14.4G
                 &#9500;&#9472;sda1 ext4         /           13.4G
                 &#9500;&#9472;sda2                             1K
                 &#9492;&#9472;sda5 swap         [SWAP]      1013M

---

### Post by sudodus on 2015-12-09
> **s9032g@comcast.net said:**
> Yes. Thank you. I have done all that prior to posting the thread.

Zero recognition. The SD card is recognized by, for example, my camera (test)

> **s9032g@comcast.net said:**
> ```
Model: ATA STEC PATA 16GB (scsi)
Disk /dev/sda: 15.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.3GB  14.3GB  primary   ext4            boot
 2      14.3GB  15.4GB  1062MB  extended
 5      14.3GB  15.4GB  1062MB  logical   linux-swap(v1)


steven@steven-Inspiron-910:~$ sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
MODEL            NAME   FSTYPE LABEL MOUNTPOINT   SIZE
STEC PATA 16GB   sda                             14.4G
                 &#9500;&#9472;sda1 ext4         /           13.4G
                 &#9500;&#9472;sda2                             1K
                 &#9492;&#9472;sda5 swap         [SWAP]      1013M[
```

If zero recognition with these commands (and what is shown, Model: ATA STEC PATA 16GB (scsi), is another drive), then I'm afraid that something is damaged or broken,

- either the SD card
- or the card reader
- or the connection from the card reader to the computer's motherboard
- or some driver or firmware in the computer.

If the camera recognizes the card, your computer should at least 'see it' with the command lsusb (or maybe lspci and I think also with the other two commands (parted and lsblk))

```
lsusb
# or if the card reader is internal and connected via pci
lspci -v  # a long output
```

Otherwise there is something wrong with the card reader or the hardware or software 'behind it'. When you changed from Ubuntu to Xubuntu 14.04 LTS, did you change from Ubuntu 14.04 LTS or from some other version of Ubuntu, for example 12.04 LTS?

---

### Post by s9032g@comcast.net on 2015-12-09
Ubuntu 14.04 LTS was the one I had before.

---

### Post by s9032g@comcast.net on 2015-12-09
OK
I did some more folling around this morning and this is what I have. Looks like some recognition

```
steven@steven-Inspiron-910:~$ lsusb
Bus 001 Device 003: ID 064e:a118 Suyin Corp. 
Bus 001 Device 002: ID 7392:7622 Edimax Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
steven@steven-Inspiron-910:~$ sudo parted -ls
[sudo] password for steven: 
Model: ATA STEC PATA 16GB (scsi)
Disk /dev/sda: 15.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.3GB  14.3GB  primary   ext4            boot
 2      14.3GB  15.4GB  1062MB  extended
 5      14.3GB  15.4GB  1062MB  logical   linux-swap(v1)


Model: SD SU08G (sd/mmc)
Disk /dev/mmcblk0: 7948MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  6885MB  6884MB  primary                   boot
 2      6886MB  7947MB  1061MB  extended
 5      6886MB  7947MB  1061MB  logical   linux-swap(v1)


steven@steven-Inspiron-910:~$ sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
MODEL            NAME        FSTYPE LABEL MOUNTPOINT   SIZE
STEC PATA 16GB   sda                                  14.4G
                 &#9500;&#9472;sda1      ext4         /           13.4G
                 &#9500;&#9472;sda2                                  1K
                 &#9492;&#9472;sda5      swap         [SWAP]      1013M
                 mmcblk0                               7.4G
                 &#9500;&#9472;mmcblk0p1                           6.4G
                 &#9500;&#9472;mmcblk0p2                             1K
                 &#9492;&#9472;mmcblk0p5 swap                     1012M
steven@steven-Inspiron-910:~$
```

---

### Post by sudodus on 2015-12-09
If I understand correctly, the SD card is recognized as /dev/mmcblk0, and there are three partitions,

```

/dev/mmcblk0p1 # a primary partition, probably your root partition, but no file system is recognized by lsblk
/dev/mmcblk0p2 # an extended partition
/dev/mmcblk0p5 # a logical swap partition

```

Are there valuable data on the SD card, that are not backed up, and that you want to recover before doing anything else?

---

### Post by s9032g@comcast.net on 2015-12-10
Again my thanks.

There is nothing on the SD card.

---

### Post by sudodus on 2015-12-10
I'm still not sure why the card does not work as before, if it is a problem with some driver, or if the drive is somehow damaged. The file system of the drive might be damaged (on /dev/mmcblk0p1) and when booted from some other drive, for example from a USB boot drive, you can try to repair it. The drive must not be mounted, unmount with

```
sudo umount /dev/mmcblk0p1
```

and then run

```
sudo e2fsck -cf /dev/mmcblk0p1
```

-c means that the flash hardware is tested and bad sectors marked (to avoid using them). -f means 'force', do the checking even if the short test indicates no problem.

-o-

If the repair fails and you want an installed Ubuntu on the SD card again, you can (re-)install it like you did before, install the system like you would install into an internal drive. In this case you should be able to install into the same partitions as before for example from a USB boot drive (with Ubuntu or an Ubuntu flavour (Lubuntu, ..., Xubuntu). Use ***Something else*** at the partitioning window. Use the mount option noatime in /etc/fstab to avoid excessive wear of the root partition. Use the system in such a way, that you avoid swapping as much as possible for the same reason (but also to avoid making it slow).

-o-

If you want to use the SD card as a data card, you can create a new partition table and a FAT32 partition. gparted is a good tool for that purpose.

---

### Post by s9032g@comcast.net on 2015-12-10
OK

I went ahead fearlessly and here's the terminal

steven@steven-Inspiron-910:~$ sudo umount /dev/mmcblk0p1
[sudo] password for steven: 
umount: /dev/mmcblk0p1: not mounted
steven@steven-Inspiron-910:~$ sudo e2fsck -cf /dev/mmcblk0p1
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
Superblock has an invalid journal (inode 8).
Clear<y>? yes
*** ext3 journal has been deleted - filesystem is now ext2 only ***

Resize inode not valid.  Recreate<y>? yes
Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 errdone                                                 
/dev/mmcblk0p1: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Root inode is not a directory.  Clear<y>? yes
Deleted inode 6037 has zero dtime.  Fix<y>? yes
Deleted inode 32235 has zero dtime.  Fix<y>? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Root inode not allocated.  Allocate<y>? yes
/lost+found not found.  Create<y>? yes
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  +(0--8524) +(32768--33179) +(98304--98715) +(163840--164251) +(229376--229787) +(294912--295323) -(557056--589823) +(819200--819611) +(884736--885147) +(1605632--1606043)
Fix<y>? yes
Free blocks count wrong for group #0 (24236, counted=24241).
Fix<y>? yes
Free blocks count wrong for group #17 (0, counted=32768).
Fix<y>? yes
Free blocks count wrong (1617792, counted=1650565).
Fix<y>? yes
Inode bitmap differences:  +1 +(3--10)
Fix<y>? yes
Free inodes count wrong for group #0 (8068, counted=8069).
Fix<y>? yes
Directories count wrong for group #0 (3, counted=2).
Fix<y>? yes
Free inodes count wrong (420148, counted=420149).
Fix<y>? yes
Recreate journal<y>? yes
Creating journal (32768 blocks):  Done.

*** journal has been re-created - filesystem is now ext3 again ***

/dev/mmcblk0p1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/mmcblk0p1: 11/420160 files (0.0% non-contiguous), 62843/1680640 blocks

steven@steven-Inspiron-910:~$ 
steven@steven-Inspiron-910:~$ 

new reading unchanged
steven@steven-Inspiron-910:~$ 
steven@steven-Inspiron-910:~$ lsusb
Bus 001 Device 007: ID 7392:7622 Edimax Technology Co., Ltd 
Bus 001 Device 002: ID 064e:a118 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

My Xubuntu is not meant to be on the SD card. It is only for added memory. Never had to do a partition before. Just plug and go. I am afraid that I don't understand enough to do much more.

---

### Post by s9032g@comcast.net on 2015-12-10
Sudodus

After I ran what you suggested the "fix" was not apparent in terminal; however when I check my file system I now see the SD card just as I used to. Thanks for the magnificent help! This forum is made great by people like you.

---

### Post by sudodus on 2015-12-10
***Edit:*** Congratulations :KS

Ignore the part of this post below the horizontal line (I posted while you wrote post #12)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

[hr][/hr]
1.Please unplug and re-plug the SD card now

2. Run 

```
sudo parted -ls

sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
```

What is the output? Is the file system in mmcblk0p1 recognized now?

-o-

If you want to use the SD card only as added memory, I suggest that you edit the partition table with ***gparted***. That will make things much simpler. Make one big partition and create a **FAT32** file system in it.

---

### Post by s9032g@comcast.net on 2015-12-11
Sorry I don't understand what to put in here

sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE

---

### Post by sudodus on 2015-12-11
It is a command line (that you write in a terminal window). You may be asked to enter your user's password to get superuser access (sudo). After that the listed data (MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE ) of all the connected mass storage devices will be printed to the screen.

```
lsblk -h
``` will print a list of possible data to select for printing.

---

### Post by s9032g@comcast.net on 2015-12-11
Heres what I get. Just general information

Available columns:
       NAME  device name
      KNAME  internal kernel device name
    MAJ:MIN  major:minor device number
     FSTYPE  filesystem type
 MOUNTPOINT  where the device is mounted
      LABEL  filesystem LABEL
       UUID  filesystem UUID
         RO  read-only device
         RM  removable device
      MODEL  device identifier
       SIZE  size of the device
      STATE  state of the device
      OWNER  user name
      GROUP  group name
       MODE  device node permissions
  ALIGNMENT  alignment offset
     MIN-IO  minimum I/O size
     OPT-IO  optimal I/O size
    PHY-SEC  physical sector size
    LOG-SEC  logical sector size
       ROTA  rotational device
      SCHED  I/O scheduler name
    RQ-SIZE  request queue size
       TYPE  device type
   DISC-ALN  discard alignment offset
  DISC-GRAN  discard granularity
   DISC-MAX  discard max bytes
  DISC-ZERO  discard zeroes data

ALSO how can I get the SD to mount automatically? Now  I have to enter my password every time I signon

---

### Post by sudodus on 2015-12-11
> **s9032g@comcast.net said:**
> Sorry I don't understand what to put in here

sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE

Simply copy and paste the command line into a terminal window and press Enter to run it. (Enter sudo password - there is no echo, but enter your usual password anyway and press Enter)

```
sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
```

(Or maybe I don't understand what you want?)

---

### Post by sudodus on 2015-12-11
> **s9032g@comcast.net said:**
> ...
ALSO how can I get the SD to mount automatically? Now  I have to enter my password every time I signon

You can add a line for it in the file **/etc/fstab**

Please post the output of the command we have been discussing, this time with a column for UUID too - to show how the SD is recognized now after the repair:

```
sudo lsblk -o MODEL,NAME,**[COLOR="#0000CD"]UUID[/COLOR]**,FSTYPE,LABEL,MOUNTPOINT,SIZE
```

From that information I can help you design the line to add into the file **/etc/fstab**

---

