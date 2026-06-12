---
title: "Desperate secondary IDE drive not writable"
date: 2008-01-16
forum: General Help
---

### Post by timboellis on 2008-01-16
I have a slave drive in my PC all I want it for it to mount when my PC is loaded by me or any other users with full access to it.

It is a Fat32 drive I can mount it and see it but no write permissions.

Here is info I think that will help

[PHP]tim@Timbo:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00077a74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3   *           1       30401   244196001    5  Extended
/dev/sda5           30119       30401     2273166   82  Linux swap / Solaris
/dev/sda6               1       30118   241922740+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14310072

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488391041    c  W95 FAT32 (LBA)
[/PHP]
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda6
UUID=d59d14a2-0dc0-4eed-93fa-0522caf97786  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=17dacc52-0317-47ca-b33b-5a0735ca8413  none           swap         sw                          0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec            0  0  
/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec            0  0   
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat   user,auto,fmask=0111,dmask=0000[/PHP]

Please help I am really loosing it with it now

---

### Post by c0met on 2008-01-16
The below URL has some information on this that might be of help.

[http://ubuntuforums.org/archive/index.php/t-411966.html]("http://ubuntuforums.org/archive/index.php/t-411966.html")

---

### Post by timboellis on 2008-01-16
Thanks for the lonk but still does not help still I can see the drive but no remissions,

I get this at the final step on all th efiles

chown: changing ownership of `/media/backup/mp3/Yess - Owner Of A Lonley Heart.mp3': Read-only file system

Any other suggestions?

---

### Post by c0met on 2008-01-16
Hi Timbo,

Sorry, I don't have any other ideas for direct help. Seems to me that you probably need to research the CHMOD and/or CHOWN commands in Linux. I am not familiar with how to use these but I'd imagine that there's a lot of information on the net.

---

### Post by mathisdermaler on 2008-01-16
```

#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat   user,auto,fmask=0111,dmask=0000 

```

Concentrate on this line.  The last field is the "mount flags" and will control how the disk is mounted.  I don't have a fat partition to play with right now but you probably want to include the rw flag like this:

```

#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat   user,auto,fmask=0111,dmask=0000,rw

```

If this doesn't work, type "man mount" at your shell prompt and consult the "-o" options

---

