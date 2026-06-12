---
title: "can't boot after update"
date: 2014-12-11
forum: General Help
---

### Post by beelzebufo on 2014-12-11
This is the second time this has happened.  I update as I am prompted to, then reboot, I get to the encryption password, enter it, all is well, crypt sda5 is successfully started, then it hangs.  I can't chroot into anything from a live usb, I can't do anything.  I don't really want to fully reinstall yet again, I am not losing any data really, I just don't want to have to install everything that I just installed.  Any ideas?  

when I try to mount things, either they don't exist, or I get a "you must specify an operating system" error which I am assuming happens because of the encryption.

also, I keep getting this weird error ```
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
```  What is /cow?

Thanks
Mike

dell inspiron laptop
ubuntugnome 14.04 64 bit encrypted.

---

### Post by beelzebufo on 2014-12-11
I also can't access my home folder, I run nautilus as root and open it, there is a readme and an app in there, I click on the app, and it says that the encrypted filesystem hasn't been set up properly.  It was before, after the update, it is not, something is wonky in the ubuntu gnome updates, I have no idea what did it, but it's been there for a while as this happened to me before.  Please fix it so that I don't have to leave ubuntugnome again, I love gnome :(

here is fdisk -l if that helps

```
ubuntu-gnome@ubuntu-gnome:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0009d58b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   83  Linux

Disk /dev/sdb: 16.0 GB, 16043212800 bytes
145 heads, 31 sectors/track, 6970 cylinders, total 31334400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00076dd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     6965247     3481600    b  W95 FAT32
/dev/sdb2         6965248     6996712       15732+   c  W95 FAT32 (LBA)

Disk /dev/mapper/luks-151142e0-07f0-4e6e-91ae-5853e27682a1: 999.9 GB, 999945142272 bytes
255 heads, 63 sectors/track, 121569 cylinders, total 1953017856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/luks-151142e0-07f0-4e6e-91ae-5853e27682a1 doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--gnome--vg-root: 991.6 GB, 991600574464 bytes
255 heads, 63 sectors/track, 120555 cylinders, total 1936719872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--gnome--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--gnome--vg-swap_1: 8296 MB, 8296333312 bytes
255 heads, 63 sectors/track, 1008 cylinders, total 16203776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--gnome--vg-swap_1 doesn't contain a valid partition table
```

---

### Post by beelzebufo on 2014-12-11
after hitting esc at the encryption screen, it hangs on these two things at separate times

1: stopping system 5 runlevel compatibility
2: starting enable remaining boot-time encrypted block devices

this is on top of the errors listed above.

---

