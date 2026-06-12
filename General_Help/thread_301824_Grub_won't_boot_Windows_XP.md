---
title: "Grub won't boot Windows XP"
date: 2006-11-17
forum: General Help
---

### Post by JoeTheZombie on 2006-11-17
Hello.  My grub isn't booting Windows XP, which isn't necessarily a bad thing, but nonetheless, I need it working.  This is my first install attempt at a Linux distro, so be easy on me! I have two HDDs.  HDD1 is a PATA drive with 3 partitions:
1. Ubuntu
2. Swap
3. Data.

HDD2 is a SATA drive, with 1 XP partition.

Windows XP appears in my grub menu, but when selected, "Starting Up..." appears and never goes away.  The BIOS is set as the PATA drive as first drive, and the boot drive.  The only way I can get XP to start is to disable the PATA drive.

**menu.lst**:```

title Windows XP Professional
root (hd1,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```


**fstab**:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5a1c857d-dbef-4702-b90f-c20f16759bd3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=7CE809B7E80970A6 /data           ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=DA9006A5900687E9 /xp             ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=1c8f0e11-414b-4a42-9a52-96f29a4c7f56 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by taurus on 2006-11-17
What is the output of this command then?

```
sudo fdisk -l
```

---

### Post by JoeTheZombie on 2006-11-17
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1147     9213246   83  Linux
/dev/hda2            1276        9729    67906755    7  HPFS/NTFS
/dev/hda3            1148        1275     1028160   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10010    80405293+   7  HPFS/NTFS

```

---

### Post by bernied on 2006-11-17
Windows doesn't like to share, and doesn't cope very well with being the second operating system. Most people let windows have the first partition of the first disk for this reason. But all is not lost. Windows can be fooled into thinking it's on the first drive.

You can do this with the grub map command

I see you can look at your menu.lst file. Are you able to edit it? You will need to do this as the root user. Easiest (for me) way to do this is

open a terminal 
type sudo nano /boot/grub/menu.lst

edit the windows entry so it looks like this:

title Windows XP Professional
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

(I took two lines out of your file - the first root command was superceded by the rootnoverify command and the makeactive command is for partitions that don't have the boot flag set, which your windows partition almost certainly will - you don't have to take these lines out if you don't want to)

---

### Post by garbagefan2 on 2006-11-17
[QUOTE=bernied]Windows doesn't like to share, and doesn't cope very well with being the second operating system.QUOTE]

I don't mean to interrupt this post but I don't like Micro$oft. But I have no choice but to keep Windows. Some things I do are Windows only unfortunately.

---

### Post by JoeTheZombie on 2006-11-17
**Success!**
Thank you so much, bernied.  It worked!  Woo-hoo!

garbagefan2, what is your comment supposed to mean?  bernied just fixed my installation so I can now boot WindowsXP.  The truth of the matter seems to be that XP must be on the first drive, or it won't boot.  That is not a matter of opinion, but a matter of fact.

---

### Post by bernied on 2006-11-17
> **garbagefan2 said:**
> [QUOTE=bernied]Windows doesn't like to share, and doesn't cope very well with being the second operating system.

I don't mean to interrupt this post but I don't like Micro$oft. But I have no choice but to keep Windows. Some things I do are Windows only unfortunately.[/QUOTE]
I agree with you - I also have to keep using windows, and would rather not.

I'm glad you're up and running ZombieJoe!

---

