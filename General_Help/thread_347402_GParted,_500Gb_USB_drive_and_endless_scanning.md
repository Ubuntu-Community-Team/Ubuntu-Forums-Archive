---
title: "GParted, 500Gb USB drive and endless scanning"
date: 2007-01-27
forum: General Help
---

### Post by andy gee on 2007-01-27
I have just bought a 500Gb external hard drive, using USB 2.0, to back up my internal hard drives. It is fat32, so I want to repartition to ext2 or 3 to make it a bit faster. Plus I'm having problems with rsync (although that's awhole nother story).

So I unmount the drive at /media/sda1 and get out trusty GParted 0.25 (gui).

Unfortunately, all that happens is the little time bar at the bottom moves back and forth, with the message "Scanning all devices " down the bottom. If I remount the drive, GParted finds it ok, only now of course it is locked.

I downloaded the new GParted live CD 0.3.3 to see if it made any difference - no change.

Anyone help me on this one? How can I reformat/repartition my external 500Gb harddrive from fat32 to ext2?

Thanks....

---

### Post by dcstar on 2007-01-27
> **andy gee said:**
> 
.......
Anyone help me on this one? How can I reformat/repartition my external 500Gb harddrive from fat32 to ext2?

Thanks....
```
man mke2fs
```

---

### Post by andy gee on 2007-01-29
Ok, read the mke2fs man, and gave it a go from command line:

```
andy@andy-desktop:~$ mke2fs /media/sda1
mke2fs 1.39 (29-May-2006)
/media/sda1 is not a block special device.
Proceed anyway? (y,n) y
mke2fs: Device size reported to be zero.  Invalid partition specified, or
        partition table wasn't reread after running fdisk, due to
        a modified partition being busy and in use.  You may need to reboot
        to re-read your partition table.
```


So I tried to force it:

```
andy@andy-desktop:~$ mke2fs -F /media/sda1
mke2fs 1.39 (29-May-2006)
mke2fs: Device size reported to be zero.  Invalid partition specified, or
        partition table wasn't reread after running fdisk, due to
        a modified partition being busy and in use.  You may need to reboot
        to re-read your partition table.
```


So finally I ran fsck:

```
andy@andy-desktop:~$ fsck /media/sda1
fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:42/4e, 72:41/4f, 73:43/20, 74:4b/4e, 75:55/41, 76:50/4d, 77:20/45
  , 78:35/20, 79:30/20, 80:30/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
/200g_drive_backup/storage/Linux_isos/ix86/.KNOPPIX_V5.1.0DVD-2006-12-30-EN.iso.GPWwvG
  File size is 4294967295 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
Leaving file system unchanged.
/dev/sda1: 112832 files, 701764/15258274 clusters
```

and ran mke2fs again:

```
andy@andy-desktop:~$ sudo mke2fs /media/sda1
mke2fs 1.39 (29-May-2006)
/media/sda1 is not a block special device.
Proceed anyway? (y,n) y
mke2fs: Device size reported to be zero.  Invalid partition specified, or
        partition table wasn't reread after running fdisk, due to
        a modified partition being busy and in use.  You may need to reboot
        to re-read your partition table.
```

Help please! ](*,)

---

### Post by andy gee on 2007-01-29
Ah, well it would have worked if I was trying to mke2fs /dev/sda1 instead of /media/sda1 which I had just unmounted! n00b alert!

....and....


it worked!

---

