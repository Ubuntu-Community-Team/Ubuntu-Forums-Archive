---
title: "UUIDs in mdadm and fstab"
date: 2007-10-20
forum: General Help
---

### Post by ultralame on 2007-10-20
I have searched through and unfortunately not found the full answers to the problem I am having.

Essentially, my Feisty system assigns my hard drives differently each time it boots, depending on what's connected at boot up.  All disks are SATAs, on two different controllers, with one PATA CDROM.  I sometimes have flash drives connected or FireWire drives too.

The first disk connected to the first controller is my boot disk, normally sda.  I have 6 other disks used in a RAID5 array (4+1+1 spare, 2 partitions on each disk => md0 and md1).

The serious problem is that I created the RAID array using mdadm and dev names.  When I did that, sda was the boot, and I created the array using /dev/sdb-sde then added sdf as the parity drive then added /sdg as the spare.

If something else is attached to the system when it boots, the drive assignments get shifted.  sda -> sdd or sdc, etc.  The machine boots fine, but mdadm can start the array assuming that the SPARE is one of the 5 array drives; and immediately starts to rebuild the array on the spare.  The former array member drive then becomes the spare.  This is annoying, to say the least.

I think that I can protect myself by using UUIDs in fstab and mdadm.  I have the info I need for fstab (UUIDs for the boot drive partitions and /dev/md0, dev/md1).

BUT what about mdadm?

1) Is it possible to create an array by specifying UUIDs for the partitions instead of device names?
2) Can I change my existing array definition(s) without killing it first?
3) Most importantly, how can I find the UUIDs for all my partitions?

/dev/disk/by-uuid only lists partitions for /dev/sda1, sda5, md0 and md1.  Does not list the partitions that make up my two RAID5 partitions.

blkid lists some, but not all.   But from what I have read, I might not be able to trust it.

vol_id -u /dev/sdb1 doesn't do anything.

Some info follows:
(For this info, my boot drive was assigned /dev/sdd; It had beed /dev/sda when I originally created the RAID array).

$ sudo fdisk -l
```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1521    12217401   fd  Linux raid autodetect
/dev/sda2            1522       30401   231978600   fd  Linux raid autodetect

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1521    12217401   fd  Linux raid autodetect
/dev/sdb2            1522       30401   231978600   fd  Linux raid autodetect

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1521    12217401   fd  Linux raid autodetect
/dev/sdc2            1522       30401   231978600   fd  Linux raid autodetect

Disk /dev/md0: 50.0 GB, 50041978880 bytes
2 heads, 4 sectors/track, 12217280 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 950.1 GB, 950183919616 bytes
2 heads, 4 sectors/track, 231978496 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       14219   114214086   83  Linux
/dev/sdd2           14220       14593     3004155    5  Extended
/dev/sdd5           14220       14593     3004123+  82  Linux swap / Solaris

Disk /dev/sde: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        1521    12217401   fd  Linux raid autodetect
/dev/sde2            1522       30401   231978600   fd  Linux raid autodetect

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        1521    12217401   fd  Linux raid autodetect
/dev/sdf2            1522       30401   231978600   fd  Linux raid autodetect

Disk /dev/sdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        1521    12217401   fd  Linux raid autodetect
/dev/sdg2            1522       30401   231978600   fd  Linux raid autodetect
```

$ blkid
```
/dev/md1: UUID="9b275471-c610-46a3-aafe-5f420e0c7775" TYPE="ext2"
/dev/sdd2: UUID="9b275471-c610-46a3-aafe-5f420e0c7775" TYPE="ext2"
/dev/sdc1: UUID="d957e753-1105-4d00-99a8-5cd24e41dab4" TYPE="ext2"
/dev/sdc2: UUID="9ba7857e-c310-87e5-17fe-5f420e0c7775" TYPE="ext2"
/dev/sdd5: UUID="c956c71e-dd6c-4430-9b8e-d98026c03760" TYPE="swap"
/dev/sde1: UUID="d957e753-1105-4d00-99a8-5cd24e41dab4" TYPE="ext2"
/dev/sde2: UUID="9b275471-c610-46a3-aafe-5f420e0c7775" TYPE="ext2"
/dev/md0: UUID="d957e753-1105-4d00-99a8-5cd24e41dab4" TYPE="ext2"
/dev/sdd1: UUID="e69f1ea9-78d0-4291-aa30-1068cb7a1953" SEC_TYPE="ext2"  TYPE="ext3"
```

$ ls -lah /dev/disk/by-uuid/
```
total 0
drwxr-xr-x 2 root root 120 2007-10-17 20:14 .
drwxr-xr-x 5 root root 100 2007-10-17 20:21 ..
lrwxrwxrwx 1 root root   9 2007-10-17 20:14 9b275471-c610-46a3-aafe-5f420e0c7775 -> ../../md1
lrwxrwxrwx 1 root root  10 2007-10-17 20:21 c956c71e-dd6c-4430-9b8e-d98026c03760 -> ../../sdd5
lrwxrwxrwx 1 root root   9 2007-10-17 20:14 d957e753-1105-4d00-99a8-5cd24e41dab4 -> ../../md0
lrwxrwxrwx 1 root root  10 2007-10-17 20:21 e69f1ea9-78d0-4291-aa30-1068cb7a1953 -> ../../sdd1
```

One mdadm call to one of the RAID partitions:
$ sudo mdadm -E /dev/sda1
```
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e7356e2b:71e53a26:94b87bc7:e6a9e6b2
  Creation Time : Sat Apr  7 23:32:58 2007
     Raid Level : raid5
    Device Size : 12217280 (11.65 GiB 12.51 GB)
     Array Size : 48869120 (46.61 GiB 50.04 GB)
   Raid Devices : 5
  Total Devices : 6
Preferred Minor : 0

    Update Time : Wed Oct 17 20:30:13 2007
          State : clean
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1
       Checksum : be28e17 - correct
         Events : 0.2601800

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8        1        5      spare   /dev/sda1

   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       97        3      active sync   /dev/sdg1
   4     4       8       33        4      active sync   /dev/sdc1
   5     5       8        1        5      spare   /dev/sda1
```

---

### Post by hotdoog on 2008-06-07
I have the same problem and a partial workaround. I came across this looking for help but what I've learned so far may help. I figured this out from [http://www.reactivated.net/writing_udev_rules.html]("http://www.reactivated.net/writing_udev_rules.html")

I've been using the udev symlinks to the device serial number/partition information. I had been, like you are, trying to use UUID or disk label to assign the partitions that make up my raid5 array. This because I have the same problem as you that the drive letters (I have 4 drives) are assigned inconsistently each boot. Using LABEL or UUID in the fstab is quite effective. However with the raid the filesystem info (superblock I think) of the component partition isn't readable so there is no way to use label or uuid. There is a uuid for the combined array: md0 md1 etc but that isn't useful

It turns out you can find udev symlinks to the normal drive letters for things besides just uuid and disklabel. In fact this seems to be the backend to the uuid and disklabel system.

So, instead of /dev/sd## you have a /dev/disk/by-id/###...

To find these use
```
ls -lR /dev/disk
```
or for a perticular device such as sda
```
udevinfo -a -p /sys/block/sda
```

Then you can find a link to find the partition you want even if the disks are re-ordered and even if the partition superblock isn't functioning.

For example for myself I replaced **/dev/sda2** with
**/dev/disk/by-id/ata-ST3300622AS_3NF1NCLB-part2**

I don't know if this is the proper way to do this but it does seem to be working. I was also able to use this to mount my swap partition and a msdos FAT32 filesystem which also weren't working with LABEL or UUID in the fstab.

The problem with doing this - for me so far - is that the raid still isn't starting on boot. I don't know why this is because I'm too new to mdadm - this is my first RAID. I get different errors for my md0 and md1... Not exactly sure why. In any case I'm easily able to get the array going using the mdadm assemble command

```
mdadm /dev/md0 -A /dev/disk/by-id/diskserial#andpartion...repeated for each partition
```

Hope that is helpful to someone though this thread seems dead. If anyone knows why mdadm isn't mounting for me that would be helpful. When I do 
```
mdadm -D /dev/md0 /dev/md1
```
I get the list of partitions in the lettered sda sdb format. So I don't know if that means that mdadm isn't remembering the serial numbers /dev/disk/by-id i am passing to it.

I guess if I don't figure it out I could always put the mdadm assemble commands into a boot script.

---

