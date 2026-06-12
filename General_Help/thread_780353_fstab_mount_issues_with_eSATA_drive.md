---
title: "fstab mount issues with eSATA drive"
date: 2008-05-03
forum: General Help
---

### Post by DaddyX3 on 2008-05-03
I'm using Ubuntu 8.04 final release, and can not mount my eSATA using the name I supplied to my /media director or fstab. Here is my drive listings: 
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00086b8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       77825   625129281   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6849    55014561    7  HPFS/NTFS
/dev/sdb2            6850       10496    29294527+  83  Linux
/dev/sdb3           10497       19457    71979232+   5  Extended
/dev/sdb5           10497       14143    29294496   83  Linux
/dev/sdb6           14144       18884    38082051   83  Linux
/dev/sdb7           18885       19457     4602591   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076c34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2432    19535008+  83  Linux
/dev/sdc2           10233       12664    19535040   83  Linux
/dev/sdc3            2433       10232    62653500    5  Extended
/dev/sdc4           12665       14488    14651280   83  Linux
/dev/sdc5            2433        4864    19535008+  83  Linux
/dev/sdc6            4865        9727    39062016   83  Linux
/dev/sdc7            9728       10232     4056381   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aa1da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001   83  Linux

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01190c64

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001   83  Linux

Disk /dev/md0: 500.1 GB, 500113211392 bytes
2 heads, 4 sectors/track, 122097952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
zzmadi@zzmadi-desktop:~$ 

```
Another problem is that the 640GB drive /dev/sda in the above is my eSATA drive and it keeps changing spots on me! its usually /dev/sde instead. This is a problem as well and any info on how to lock it into /dev/sde all the time would be welcome!!! 

Here is my /etc/fstab file: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d6a951dd-018b-4c96-89eb-31d1e89835b7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=87f3aef9-9e2a-47af-8722-f427e47016c3 /home           ext3    relatime        0       2
# /dev/sda6
UUID=bcb83959-9e03-4406-ae53-978b81ed8cb1 /****           ext3    relatime        0       2
# /dev/sda7
UUID=8a371597-3b30-42de-9af9-a8db2bf3969f none            swap    sw              0       0
# /dev/sdb7
UUID=fdf7cc93-2483-49bc-a196-48cae14287a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/md0	/media/bigdaddy	ext3	defaults	0	2
/dev/sde1	/media/eSATA	ext3 	defaults 	0	2

```
Mind you that I'm fully aware of the problem with the above combination of what is currently mounted and what is listed in my fstab file. This can be fixed and I have gone around and around with them both. For example: If I changed my bottom line right now to: 
```
/dev/sda        /media/eSATA      ext3     defaults     0       2 
```
 One would think that my 640GB eSATA drive would then mount to /media/eSATA. Well ..... it doesn't! I can do a manual sudo mount -a and it will mount and show up on the desktop as a "640GB drive" but not under the name "eSATA". I have also edited my fstab to read /dev/sde1 instead of just /dev/sda but it make no difference. It refuses to mount to /media directory and it is changing /dev names, any ideas??? I also am having a problem during boot up because it is not getting mounted like it should from the fstab listing. 
Thanks for you time and any ideas:)

---

### Post by bodhi.zazen on 2008-05-03
This is part of the reason you may want to mount the device by UUID or label (the /dev/sdxy may change).

To list your partitions by UUID :

```
sudo blkid
```Your fstab entry then becomes:

```
UUID=xxx.yyy.zzz  /media/eSATA     ext3 auto,user      0       2
```

Note: blkid uses quotes, " " , surrounding the UUID, fstab does not.

---

### Post by DaddyX3 on 2008-05-03
Thank you very much for the post and info. I have one more question for you. Why does it not take on the mame supplied in the fstab file? (eSATA) The directory exists, the drive mounts and it is labled "640.1GB Media" instead of "eSATA". Just curious cause my raid 0 array (md0) mounts and labels itself correctly. Why does it not label corectly? any ideas?

---

### Post by soxs on 2008-05-03
It is like cubing what letter X in /dev/sdX gets (In fact it is somwhat ruled by the the detection, which usb device will be detectet first, second, third ..etc). So you it may or may not mount.

---

### Post by DaddyX3 on 2008-05-03
Does this mean that an externally connected device like eSATA cant have a stable place to mount to? In other words, because it is an esata device it will be treated like a usb device?

---

### Post by soxs on 2008-05-04
At lesat it seems to be like that.

---

### Post by fjgaude on 2008-05-06
Say, don't you connect to the eSATA drive through the use of a SATA controller, not through the USB channels?

Find out what the eSATA drive UUID is and use that in the fstab file. That should do it.

---

