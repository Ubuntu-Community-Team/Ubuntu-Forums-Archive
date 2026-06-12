---
title: "[SOLVED] Cannot make Hard Disk AUTOmount on startup"
date: 2007-11-02
forum: General Help
---

### Post by geo909 on 2007-11-02
Hello everybody,

I need some help here:
I have Ubuntu 7.10
I have a Hard Disk which I can mount manually 
by Right-Clicking on the icon and chosing "Mount Volume"
but it would be really convenient for me to have it mounted automatically
on startup. I know I have to add aline in my fstab file, and I messed around
with a couple of HOWTOs, but I didn't manage to do anything.
Can someone please specify me exactly what line I should write down there?
Here's the details:

 Doing "fdisk" I have:
```

geo909@desktop:~$ sudo fdisk -l
[sudo] password for geo909:

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9f8a9f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdb3bdb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a2e1a2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19457   156288321    6  FAT16



```

The disk I need to be automounted on startup is the 160GB one
(No op system on, just have it for storage).

Also, here is my fstab file,in case you need it:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda1     
UUID=14062b8a-8e2e-4195-aad5-3c4bb22797e9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7fb8ac4a-2cf4-419c-9ff0-209d7f27cc1d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


```

 Any help , please?!

Thank you in advance for your time!

---

### Post by dcstar on 2007-11-02
> **geo909 said:**
> Hello everybody,

I need some help here:
I have Ubuntu 7.10
I have a Hard Disk which I can mount manually 
by Right-Clicking on the icon and chosing "Mount Volume"
but it would be really convenient for me to have it mounted automatically
on startup.
.........
 Any help , please?!

Thank you in advance for your time!

Install the **pysdm** package, then use** System-Administration-Storage Device Manager** to set all of this up for you automagically.

---

### Post by minus198 on 2007-11-02
*removed*

Edit: Hm.. noticed now that it was FAT16... I don't know how to mount that.

---

### Post by geo909 on 2007-11-02
> **dcstar said:**
> Install the **pysdm** package, then use** System-Administration-Storage Device Manager** to set all of this up for you automagically.

Yep! That did the job!!
Great that such utilities show up for
people who don't want to mess up with configuration files!

Thanks a lot!

---

### Post by enkoan on 2007-11-03
I would like to know how to do this through messing around with configuration files... could someone please post code or point me in the right direction?

---

