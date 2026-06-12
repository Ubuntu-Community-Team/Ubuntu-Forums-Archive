---
title: "Can't Access my windows partition"
date: 2006-11-29
forum: General Help
---

### Post by SmiLey497 on 2006-11-29
i tried going to my windows partition but it won't read it i get 

error: device /dev/sda1 is not removable

error: could not execute pmount

i've been able to access it in the past, why not now?

---

### Post by taurus on 2006-11-29
Did you mount it?  What are the outputs of these two commands from a terminal then?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by SmiLey497 on 2006-11-29
i mounted it when i installed edgy


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17089   137267361    7  HPFS/NTFS
/dev/sda2           29252       30401     9237375    c  W95 FAT32 (LBA)
/dev/sda3           17090       28900    94871857+  83  Linux
/dev/sda4           28901       29251     2819407+   5  Extended
/dev/sda5           28901       29251     2819376   82  Linux swap / Solaris

Partition table entries are not in disk order



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2b99ab17-ca56-410a-b3a0-d15b69bf704f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2AADA5706724046D /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4B6E-6BC0  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=8663ea4e-48e4-4e8f-bf22-7219f7b1abde none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2006-11-29
I am sorry but that is not how you mount ntfs & fat32...

```

# /dev/sda1
UUID=2AADA5706724046D  /media/sda1  ntfs  nls=utf8,umask=0222  0  0
# /dev/sda2
UUID=4B6E-6BC0  /media/sda2  vfat  iocharset=utf8,umask=000  0  0

```

---

### Post by jakev383 on 2006-11-29
> **taurus said:**
> I am sorry but that is not how you mount ntfs & fat32...

```

# /dev/sda1
UUID=2AADA5706724046D  /media/sda1  ntfs  nls=utf8,umask=0222  0  0
# /dev/sda2
UUID=4B6E-6BC0  /media/sda2  vfat  iocharset=utf8,umask=000  0  0

```

But that is exactly how mine was setup by default from a new install of Edgy as well.

---

### Post by taurus on 2006-11-29
> **jakev383 said:**
> But that is exactly how mine was setup by default from a new install of Edgy as well.
Look at the entries in his /etc/fstab and my version.  See the difference!!!

---

### Post by jakev383 on 2006-11-29
> **taurus said:**
> Look at the entries in his /etc/fstab and my version.  See the difference!!!

I'm not denying there is a difference. I'm just pointing out that my system looked EXACTLY like his (including uid 46 and  all) from a fresh install. I know what it's supposed to look like, but that's not the way it rolled out.

---

### Post by strabes on 2006-11-29
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by SmiLey497 on 2006-11-30
problem solved thanks guys

---

