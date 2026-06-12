---
title: "Mounting Problems"
date: 2007-11-24
forum: General Help
---

### Post by jlacroix on 2007-11-24
I've never had this problem before, I reinstalled Kubuntu today and know mounting drives is giving me hell.

First of all, when I try to access my Windows partition, this is what I get in Dolphin:
```
hal-storage-fixed-mount-all-options refused uid 1000
```

I get that when trying to mount usb flash drives sometimes too, it wants to mount twice and then I cannot change or add files to my flash drive.

Any idea what could be going on?

Here is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c6887e16-1f2c-4ec8-976a-87557b0f2a45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=f39f9fad-e29d-42b1-ba84-43e6038983ab none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by taurus on 2007-11-24
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by jlacroix on 2007-11-24
```
jeremy@jeremy-desktop:~$ sudo fdisk -l
[sudo] password for jeremy:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d8d9c8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38161   306528201   83  Linux
/dev/sdb2           38162       38913     6040440    5  Extended
/dev/sdb5           38162       38913     6040408+  82  Linux swap / Solaris

```

---

