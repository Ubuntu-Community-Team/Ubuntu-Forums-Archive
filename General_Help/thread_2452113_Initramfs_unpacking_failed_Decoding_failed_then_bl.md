---
title: "Initramfs unpacking failed: Decoding failed then black screen blinking cursor"
date: 2020-10-16
forum: General Help
---

### Post by brunopippo on 2020-10-16
Hi guys as the title says I havr that problem at the beginning and after run the booting it get stuck at this black screen with blinking cursor/underscore on the top left. I have tried with live disk to backup data and reinstal but I cant have access to the disk.
I dont know what to do. Can you help? I have no access to the system. Thank you in advance

---

### Post by Bashing-om on 2020-10-16
Hello brunopippo - Welcome to the forum.

Show us what you are working with drive wise:
pastebin the output - between code tags -  of terminal command:
```

sudo parted -l

```
from that live disk.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]see where we go from here
[/INDENT]

---

### Post by brunopippo on 2020-11-15
Hi I am very sorry for the delay. I have tried something different but nothing. Today it's giving me this: 
Error: Can't have overlapping partitions.
Ignore/Cancel
If I do ignore is posting results..dont know how to post a picture of it now.

---

### Post by brunopippo on 2020-11-15
Model: ATA WDC WD5000AAKX-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  882MB  881MB   primary   ntfs         boot
 2      882MB   457GB  456GB   primary   ntfs
 3      457GB   499GB  42.0GB  extended
 5      457GB   499GB  42.0GB  logical   ntfs
 4      499GB   500GB  823MB   primary   ntfs         msftres


Model: ATA MAXTOR STM325031 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   101GB  101GB   primary   ntfs
 4      101GB   101GB  537MB   primary   fat32
 3      101GB   250GB  149GB   extended
 7      101GB   149GB  48.2GB  logical   ext4
 6      149GB   246GB  96.3GB  logical   ext4
 5      246GB   250GB  4293MB  logical   linux-swap(v1)


Model: UFD 2.0 Silicon-Power4G (scsi)
Disk /dev/sdc: 4052MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  4051MB  4051MB  primary  fat32        boot, lba

---

### Post by Bashing-om on 2020-11-15
brunopippo; Hey -

I do not see where the root of the issue is, using parted -
As this is msdos partitioning, let's try with a different tool.
Post back - between code tags:
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See then if the numbers line up.

[INDENT]maybe Yes
[INDENT][INDENT]could be not so yes[/INDENT][/INDENT][/INDENT]

---

