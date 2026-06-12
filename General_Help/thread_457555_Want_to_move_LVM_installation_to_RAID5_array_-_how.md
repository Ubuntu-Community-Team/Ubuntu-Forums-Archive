---
title: "Want to move LVM installation to RAID5 array - how do I get it to boot?"
date: 2007-05-28
forum: General Help
---

### Post by nethbar on 2007-05-28
When I installed 7.04, I had it use LVM and setup on /dev/sdd1

I was never able to get LVM on RAID to work, kept giving me this error:
```
Error informing the kernel about modifications to partition /dev/md/0p1 --Invalid argument.
This means Linux won't know about changes you made to /dev/md/0p1 until you reboot -- so you shouldn't use it in any way before rebooting

```
And other wonky junk.

I have 3 additional SCSI drives, all identical in size to the first - 18 GB

I'd like to move everything over to a RAID 5 array, /dev/md0 and put /dev/sdd1 in to use as a hot spare.  

I've scoured the web and read a lot of really helpful stuff for situations not much like mine.  I've read a lot of howtos but there are two points I'm really stuck on (the rest I believe I can muck through):

1. I can't seem to format the boot partition I need on /dev/md0.  I can create a 256MB partition /dev/md0p1 in cfdisk and write the changes but when I go 
```
mrmr@ettin:/$ sudo mke2fs -j /dev/md0p1
mke2fs 1.40-WIP (14-Nov-2006)
Could not stat /dev/md0p1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

```
that's what I get

2. Once I do have a boot partition setup properly on my array, how do I copy over the boot information so it will properly boot?  I know 'cp -r /boot /(destination)' will get the files over but how do get GRUB to look in the new places?

Here's some helpful? output:
sudo fdisk -l
```
Disk /dev/sda: 18.3 GB, 18373206016 bytes
255 heads, 63 sectors/track, 2233 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2233    17936541   fd  Linux raid autodetect

Disk /dev/sdb: 18.3 GB, 18373206016 bytes
255 heads, 63 sectors/track, 2233 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2233    17936541   fd  Linux raid autodetect

Disk /dev/sdc: 18.3 GB, 18373206016 bytes
255 heads, 63 sectors/track, 2233 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2233    17936541   fd  Linux raid autodetect

Disk /dev/sdd: 18.3 GB, 18373206016 bytes
255 heads, 63 sectors/track, 2233 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          31      248976   83  Linux
/dev/sdd2              32        2233    17687565    5  Extended
/dev/sdd5              32        2233    17687533+  8e  Linux LVM

Disk /dev/md0: 36.7 GB, 36733845504 bytes
2 heads, 4 sectors/track, 8968224 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1   *           1       62253      249010   83  Linux

```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/ettin-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdd1
UUID=1c481e0a-0622-4c41-a5e2-724f30ab554e /boot           ext3    defaults        0       2
/dev/mapper/ettin-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0 

```

sudo mdadm --detail /dev/mdo
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon May 28 15:15:58 2007
     Raid Level : raid5
     Array Size : 35872896 (34.21 GiB 36.73 GB)
    Device Size : 17936448 (17.11 GiB 18.37 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon May 28 18:50:12 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 29827358:01a00be2:be10abfe:aadb887b (local to host ettin)
         Events : 0.8

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1

```

here's the default entry for GRUB
```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd3,0)
kernel          /vmlinuz-2.6.20-15-generic root=/dev/mapper/ettin-root ro quiet splash
initrd          /initrd.img-2.6.20-15-generic
quiet
savedefault

```

Thanks for looking!

---

### Post by fanatik on 2007-05-29
just fyi /boot can't be on lvm, you'll need a dedicated filesystem for that, else it won't be able to read the files required for start up.

---

### Post by nethbar on 2007-05-29
Yeah, I know.  That's why I'm trying to get /boot setup on md0 first, then move my LVM over.  Moving just a data partition looks pretty simple but I haven't been able to find how to move a bootable partition to a new disk/arrary properly.

I'd be happy with RTFM as long as someone can point me towards the right manual.

---

### Post by fanatik on 2007-05-29
this might be useful:

[http://tldp.org/HOWTO/Software-RAID-HOWTO-7.html#ss7.3]("http://tldp.org/HOWTO/Software-RAID-HOWTO-7.html#ss7.3")

---

