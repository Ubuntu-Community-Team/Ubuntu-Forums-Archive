---
title: "Can't mount SATA hard drive"
date: 2007-02-18
forum: General Help
---

### Post by B. W. on 2007-02-18
I "downgraded" to Edgy from Feisty Fawn (reinstalled the entire operating system), but now I can't mount my hard drive with Windows on it.

I have a 320GB SATA hard drive with Windows XP (NTFS partition, should be sda1).

I installed Edgy on my 250GB SATA hard drive.

I tried using this command after I created the 'Windows' under media:
```
sudo mount /dev/sda1 /media/Windows
```
I don't receive any errors, but the drive doesn't show up in Nautilus or the desktop, and trying the command again gives me this:
```
mount: /dev/sda1 already mounted or /media/Windows busy
mount: according to mtab, /dev/sda1 is already mounted on /media/Windows

```
If I try to unmount it, the terminal gives me an error saying the drive isn't mounted.

Here's what fdisk -l gives me:
```

Note: sector size is 2048 (not 512)

Disk /dev/sdd: 30.0 GB, 30005819392 bytes
255 heads, 63 sectors/track, 911 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1           3       96264    0  Empty
/dev/sdd2               4         912    29206170    b  W95 FAT32

```

And here's my fstab output:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1 -- converted during upgrade to edgy
UUID=adf050e5-bc20-438c-92e0-9d2138cb04f7 / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb5 -- converted during upgrade to edgy
UUID=6170ce69-6886-401d-8b7d-3f052f48687d none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[B]# /dev/sda1
/dev/sda1    /media/Windows ntfs  nls=utf8,umask=0222 0    0[/B]

```

Anyone have any ideas?

EDIT: Fixed. I don't know why it didn't work.

---

### Post by gruffy-06 on 2007-02-21
This is natural when you use a development version of Ubuntu. Do expect to encounter bugs, but do expect them to be fixed within a few days or so.

---

