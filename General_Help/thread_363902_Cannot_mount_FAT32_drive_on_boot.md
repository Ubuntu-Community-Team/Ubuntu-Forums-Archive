---
title: "Cannot mount FAT32 drive on boot"
date: 2007-02-17
forum: General Help
---

### Post by XtremeSki2001 on 2007-02-17
Ok ... I've followed a few guides, but in the interim, I think I may have messed up.

I'm running edgy.

Heres my fstab file:
```

# /etc/fstab: static file system information.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a9e36b46-1666-4da5-9354-e5c83289f6f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=49ae5e70-ecdb-4e11-8774-2468974fc865 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1    /media/windows vfat  iocharset=utf8,umask=000  0    0
```

It doesn't mount on boot.  Right now, it's not showing-up, but if I restart it will probably show and then tell me only root can mount the drive.

It's an external USB2.0 WD 250GB FAT32 drive.

Thanks for any help.  This is the only thing remaining and then I can fully switch over to Ubuntu.

---

### Post by donkey42 on 2007-02-17
well personally i set a drive as "mounted at boot" i enable Start at boot in system settings

---

### Post by XtremeSki2001 on 2007-02-20
> **donkey42 said:**
> well personally i set a drive as "mounted at boot" i enable Start at boot in system settings

Where are the settings you speak of?

I looked around and didn't see anything that allowed me to tweek hard-drive mounting.

Anyone else?

---

### Post by taurus on 2007-02-20
What are the outputs of these two commands from a terminal?

```
sudo fdisk -l
ls -la /media
```

---

### Post by donkey42 on 2007-02-20
> **XtremeSki2001 said:**
> Where are the settings you speak of?K menu > System Settings > Disk & Filesystem > Admin > then select the mount point and click Modify and check start on boot, this is not the official way to do it, but it works well

---

### Post by XtremeSki2001 on 2007-04-07
> **taurus said:**
> What are the outputs of these two commands from a terminal?

```
sudo fdisk -l
ls -la /media
```

**Sorry for the delayed reply ... I'm having so many issues, I haven't had time to tinker.**

```
erich@erich-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9541    76638051   83  Linux
/dev/hdb2            9542        9729     1510110    5  Extended
/dev/hdb5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)
erich@erich-desktop:~$ 
```

```
erich@erich-desktop:~$ ls -la /media
total 28
drwxr-xr-x  7 root root 4096 2007-01-14 08:28 .
drwxr-xr-x 21 root root 4096 2007-01-14 11:26 ..
lrwxrwxrwx  1 root root    6 2007-01-13 14:23 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-01-13 14:23 cdrom0
drwxr-xr-x  2 root root 4096 2007-01-13 14:23 cdrom1
lrwxrwxrwx  1 root root    7 2007-01-13 14:23 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-01-13 14:23 floppy0
drwxr-xr-x  2 root root 4096 2007-01-14 08:28 My Book
drwxr-xr-x  2 root root 4096 2007-01-14 08:28 windows
erich@erich-desktop:~$ 
```

[B]Now here's what I don't get.  I just started Edgy and all was well, my 250GB FAT32 drive mounted, great!  BUT, my sound wouldn't work (as it had in the past).  I reboot to see if this fixes the issue, but to no avail ... and of course now the US FAT32 250GB hard drive isn't mounted.  This is acting a lot like Windows!

Also, can't for the life of me get my Windows partition to be viewed either.

ANY help would be greatly appreciated ... these are my two biggest hurdles before switching to Ubuntu from MS.

Lastly, I installed the GMAIL notification icon and accidentally remove it from my taskbar, but I guess there is no simple way of getting it back?  I've looked around and again, no luck.

THANKS!

edit:  Here is my current FSTAB[/B]

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a9e36b46-1666-4da5-9354-e5c83289f6f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=49ae5e70-ecdb-4e11-8774-2468974fc865 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1    /media/windows vfat  iocharset=utf8,umask=000  0    0
```

---

### Post by XtremeSki2001 on 2007-04-08
BUMP

Taurus?

---

