---
title: "Grub doesn't load XP, just reboots itself"
date: 2008-01-24
forum: General Help
---

### Post by joesmoe10 on 2008-01-24
Ok, so I have Kubuntu installed with grub installed on the MBR which for me is (hd0,1)
Any time I try and boot into windows xp, grub just restarts itself and I see the same screen with the countdown timer.  So far I've tried fixmbr with the windows cd and I've tried changing some parameters in menu.lst  Any other ideas

Here's some info
$ sudo fdisk -l
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe316e316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15        2625    20972857+   7  HPFS/NTFS
/dev/sda3            2626        6516    31254457+   7  HPFS/NTFS
/dev/sda4            6517       12161    45343462+   5  Extended
/dev/sda5            6517        9068    20498908+  83  Linux
/dev/sda6            9069        9594     4225063+  82  Linux swap / Solaris
/dev/sda7            9595       12161    20619396    b  W95 FAT32

```

$ cat /boot/grub/menu.lst
```

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4f69c77a-8f7f-4d53-8b23-e101e193a509 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4f69c77a-8f7f-4d53-8b23-e101e193a509 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

$ cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=4f69c77a-8f7f-4d53-8b23-e101e193a509 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D6-0610  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=C24C76604C764EE3 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=944478B744789E24 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=4796-3011  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=3853dec4-c93f-4f66-8a9a-ce0356a4c865 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Any ideas?

---

### Post by y-lee on 2008-01-25
Try [Super Grub Disk]("http://supergrub.forjamari.linex.org/"), it ca nusually fix boot problems as well as boot any of the OSes installed.

---

