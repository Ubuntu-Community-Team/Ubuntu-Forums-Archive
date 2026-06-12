---
title: "USB Flash Drive write access from Xubuntu"
date: 2006-10-18
forum: General Help
---

### Post by textguru on 2006-10-18
I have USB flash drive that I frequently use on my Windows computer. I want to transfer file from xubuntu to other xubuntu machine and windows xp but it seems that usb flash drive only have read access. According to the error, I have a read-only file system. Is it possible for me to copy files from xubuntu machines to usb flash drive?

---

### Post by Kateikyoushi on 2006-10-18
Yes it is possible to write to the disc, but most likelyif you used it with XP it is formatted as ntfs.

Could you post the output of this command ?
```
cat /etc/fstab
```

---

### Post by textguru on 2006-10-18
xubuntu@mypc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by mcduck on 2006-10-18
It's a USB drive, so it's not in fstab. Running 'fdisk -l' should give info about it ;)

---

### Post by textguru on 2006-10-18
Your right! that why I cannot see the USB on the list. Anyway here is the output of fdisk -l:

> ubuntu@mypc:~$ sudo fdisk -l

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2376    19085188+  83  Linux
/dev/hdc2            2377        2434      465885    5  Extended
/dev/hdc5            2377        2434      465853+  82  Linux swap / Solaris

Disk /dev/sda: 512 MB, 512999424 bytes
255 heads, 63 sectors/track, 62 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+   7  HPFS/NTFS
ubuntu@mypc:~$

---

### Post by Kateikyoushi on 2006-10-18
Why isn't it in fstab if it is a usb drive ?

Let's create the directory to mount to.
```
sudo mkdir /media/sda1
```

The directory might exist already.
Then try to mount.

```
sudo mount /dev/sda1 /media/sda1 -t ntfs -o nls=utf8,umask=0222
```

---

### Post by kwrxxx on 2006-10-18
```

Device Boot Start End Blocks Id System
/dev/sda1 1 62 497983+ 7 HPFS/NTFS

```
 This shows the USB drive and it is formatted in NTFS format. You could format it to FAT32 very easily in Windows. Just copy everything to your HD from the USB stick and and then in the My Computer folder select the device and format as FAT32. If you have an specialized programs that run when you plug in the USB device they may no longer function in windows.

---

### Post by Kateikyoushi on 2006-10-18
Seems I confused it with another thread notice the flash word in the title -_-;; I thought it is a usb hard drive.

Formatting it as fat will indeed make your life easier.

---

### Post by mcduck on 2006-10-18
> **Kateikyoushi said:**
> Why isn't it in fstab if it is a usb drive ?

Because removable drives don't need an entry in fstab, as Ubuntu smartly handles them in a different way.

Anyway, the problem here is that the flash drive is formatted in NTFS, and write support for that is still at rather experimental stage (because Microsoft refuses to release any specs about NTFS).

The solution is to format the flash disk to FAT32. After that it will work on any OS, not just Windows.

---

