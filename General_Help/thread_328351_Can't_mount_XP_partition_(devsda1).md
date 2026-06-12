---
title: "Can't mount XP partition (/dev/sda1)"
date: 2006-12-30
forum: General Help
---

### Post by 0MG on 2006-12-30
I'm having problems mounting my XP partitions in Ubuntu. XP boots fine by itself, but everytime I restart after using XP, I get a grub error and have to reinstall grub.

My XP partitions are /dev/sda1 and /dev/sda2. Both are ntfs.

When I try mount -a I get:

-------
# mount -a
mount: special device /dev/sda1 does not exist
mount: special device /dev/sda2 does not exist
-------
Here's fdisk -l:
---------
# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686   42  SFS
/dev/sda2            5100        9729    37190475   42  SFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3647    29294496   83  Linux
/dev/sdb2            3648        3769      979965   82  Linux swap / Solaris
/dev/sdb3            3770        4534     6144862+  83  Linux
/dev/sdb4            4535        7084    20482875   83  Linux
-----------
I've done a couple changes to my fstab and nothing has worked. Here's what it looks like currently:
----------------
# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=4606f024-951f-425a-bcc7-b70975211247 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=90FC88B6FC88985C /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
#UUID=750e9545-b39c-466c-a92e-e27c0654a313 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /media/sda1 ntfs nls=utf8,umask=0222 0 0
/dev/sda2 /media/sda2 ntfs nls=utf8,umask=0222 0 0
---------

Here's something that looks promising but I have no idea how to attack it:

------------

# dmesg | grep sda
[17179575.636000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179575.636000] sda: Write Protect is off
[17179575.636000] sda: Mode Sense: 00 3a 00 00
[17179575.636000] SCSI device sda: drive cache: write back
[17179575.636000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179575.636000] sda: Write Protect is off
[17179575.636000] sda: Mode Sense: 00 3a 00 00
[17179575.636000] SCSI device sda: drive cache: write back
[17179575.636000]  sda:<3>ldm_parse_privhead(): Cannot find PRIVHEAD structure. LDM database is corrupt. Aborting.
[17179575.656000] sd 0:0:0:0: Attached scsi disk sda

---------------------


Any advice?

---

### Post by bulldog on 2006-12-30
Take a look at your file system,it seems to be SFS,what ever that may be,and listed as NTFS in your fstab.
And why is the swap commented out?

What are the other linux partitions?
Why is sda1 mounted twice?

Make your fstab in order so it compares with menu.lst and see what happens.
Have no idea what SFS file system is,maybe you can enlighten me?

---

### Post by 0MG on 2006-12-30
Thank you for the response.

I did a quick update and it seems that fstab knows as much about sfs as you or I.

# mount -a
mount: unknown filesystem type 'sfs'
mount: unknown filesystem type 'sfs'

](*,)

---

### Post by bulldog on 2006-12-30
Copy the valuable data from the windows disk if possible,and maybe a format and a reinstall will clear things up.

---

### Post by 0MG on 2006-12-30
> **bulldog said:**
> Take a look at your file system,it seems to be SFS,what ever that may be,and listed as NTFS in your fstab.
And why is the swap commented out?

What are the other linux partitions?
Why is sda1 mounted twice?

I commented out the original sda1 mount as it didn't work and I wanted to try something else. That was put in there during the install of edgy.

No need for swap, have 2GB ram.

---

### Post by 0MG on 2006-12-30
I was hoping that I wouldn't have to format. Any other advice?

---

### Post by computerdork on 2007-02-10
> **0MG said:**
> 
[17179575.636000] sda: Write Protect is off
[17179575.636000] sda: Mode Sense: 00 3a 00 00
[17179575.636000] SCSI device sda: drive cache: write back
[17179575.636000]  sda:<3>ldm_parse_privhead(): Cannot find PRIVHEAD structure. LDM database is corrupt. Aborting.


I was getting a similar error, and was unable to mount my raid array. fdisk showed the correct partition size, but listed its format as SFS. I knew the partition was really ext3, so I just changed the type with fdisk to linux (hex 83 i think). Sense, I am able to mount the partition normally. I don't know if it will work with NTFS the same way, but it might be worth a shot.

---

