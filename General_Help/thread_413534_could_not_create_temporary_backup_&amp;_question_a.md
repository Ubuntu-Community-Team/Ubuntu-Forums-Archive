---
title: "could not create temporary backup &amp; question about vfat partitions"
date: 2007-04-19
forum: General Help
---

### Post by finer recliner on 2007-04-19
when saving plain text files to my SD card, i always get an annoying warning about not being able to create a temporary backup first. i'm using gedit. is there anyway to disable this warning, or do i need to change my permissions for the device? or another ideA?

see attachment for screenshot of it

fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
#/dev/mmcblk0p1  /media/mmcblk0p1 vfat    defaults,utf8,umask=007,gid=46 0  1
/dev/mmcblk0p1  /media/SDcard vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda1 /media/windows ntfs umask=0222 0 0
/dev/sda1 /media/windows ntfs-3g umask=0000 0 0
/dev/sdb1 /media/External\ HDD ntfs-3g umask=0000 0 0

```
mmcblk0p1is my SD card.



second question: what is vfat? i remember when i first formated my SDcard. i used partition magic (in windows) and choose fat32 so i could read/write between linux and windows easily. however in fstab its a vfat format. and fdisk says its FAT16 (!?!)....so whats the deal? it cant be a normal fat32, because i did a funny test where i made a file and named it something longer than 8 characters (see attachment2). anyone think they can explain? 

thankss

---

### Post by kidders on 2007-04-20
Hi there,

> **finer recliner said:**
> when saving plain text files to my SD card, i always get an annoying warning about not being able to create a temporary backup firstI'm not quite sure whether you want to stop saving backups (which is trivial), disable the warning (which I don't think Gedit lets you do), or correct the underlying problem.

Not being able to create backup copies of files could be the result of a number of things, including:[LIST]
[*]**Having insufficient privileges.** Given the /etc/fstab you posted, that would probably mean (a) someone else mounted the sdcard, _and_ (b) you're not a member of the "plugdev" user group. It looks as though that would be the only way you *wouldn't* have full access to the directory the open file is in.
[*]**Running out of space.** There might not be enough space on the SD card to save the backup file.
[*]**Something strange**, like a hardware failure. There would be other evidence of that though, in your system logs.
[*]**File naming problems.** Afaik Gedit will probably try to save "filename" as "filename~" (at least that's the convention). Your FAT filesystem may be objecting to that, for some reason.[/LIST]> **finer recliner said:**
> what is vfat?VFAT is an implementation of the FAT filesystem group that exploits loopholes in the (rather poor) filesystem design, to allow filenames to contain more than 11 characters. Another common implementation of the same feature involves the use of extended attributes, which is the reason Linux makes the distinction.

> **finer recliner said:**
> it cant be a normal fat32, because i did a funny test where i made a file and named it something longer than 8 characters (see attachment2)Your test is a little confusing. The primary difference between FAT16 and FAT32 is that FAT32 stores cluster numbers in 32 bits, allowing filesystems to extend beyond 2GB.

I hope that helps answer some of your questions.

---

