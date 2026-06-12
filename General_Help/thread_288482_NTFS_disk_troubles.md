---
title: "NTFS disk troubles"
date: 2006-10-29
forum: General Help
---

### Post by Wylie on 2006-10-29
I have a NTFS hard disk that I'm having some trouble with. It was working fine with Dapper before, then I switched it out with another (older) hard disk to access some ancient files.

After reinstalling the NTFS disk and powering up, I have this problem:
"sudo fdisk -l" reports:

   Device Boot      Start         End      Blocks   Id  System

/dev/hdb1               1        7753    58612648+   5  Extended

Note that it says "Extended", not NTFS.

In the System/Administration/Disks dialog, I see the following info reported for Partition 1 of /dev/hdb1:

Device: /dev/hdb1
Filesystem: Windows NTFS
Access Path: /media/hdb1
Size: (Free space not available)
Status: Inaccessible ("Enable" button is live, but doesn't do anything for me, "Browse" is grayed out)

Why is fdisk telling me one thing while the Disks Manager is telling me another? At the moment, I am unable to mount the drive at all. :-k

---

### Post by joshgtv6 on 2006-10-29
i had the same issue as you.  see link below. 

[http://www.ubuntuforums.org/showthread.php?t=284685](http://www.ubuntuforums.org/showthread.php?t=284685)

try mounting the drive with both tutorials.  The one for mounting an NTFS drive and the one for mounting a Linux drive.  If you still can't get it to mount using the tutorials post up your results of fdisk and your fstab file.

EDIT: i'm heading to sleep for the night so if someone doesn't get you help tonight i'll check in the morning and post up some suggestions for you based on the fdisk and fstab info. :D

---

### Post by Wylie on 2006-10-29
Here's my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1     ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

And my fdisk -l:
```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4677    37567971   83  Linux
/dev/hda2            4678        4865     1510110    5  Extended
/dev/hda5            4678        4865     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
240 heads, 63 sectors/track, 7753 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7753    58612648+   5  Extended

```

When I try 'sudo mount -a', I get:

```
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Well, I'll bite. Here's the results of dmesg | tail:
```
[17187164.428000] EXT3-fs: unable to read superblock
[17187170.012000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17187170.012000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17187170.012000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
[17187176.368000] attempt to access beyond end of device
[17187176.368000] hdb1: rw=0, want=4, limit=2
[17187176.368000] EXT2-fs: unable to read superblock
[17187696.436000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17187696.436000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17187696.436000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
```



To reiterate, I was able to use this disk (read-only) before physically switching it out with another disk (not ntfs) earlier today. (No, I didn't do anything stupid like trying to hot-swap the hard drives, and yes, the hd is correctly physically connected- I checked all of the "dumb noob" stuff before asking the internets. :) )

I'll check this disk in another computer tomorrow to make sure that Windows can see it- right now, I'm going to bed.

---

### Post by joshgtv6 on 2006-10-30
try following the tutorial for mounting an Linux filesystem.  One of the readouts of the mount error said it wasnt' an NTFS drive.  Try mounting it as if it was a Linux filesystem.

[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by Wylie on 2006-10-30
No dice. Here's a shot of gparted - it shows all of this disk as "unallocated".

I didn't get a chance to test the disk out in another computer- that's my next move. It's unlikely that the disk went bad in the 5 minutes it was disconnected, but possible.

---

### Post by joshgtv6 on 2006-10-31
well, at this point the last suggestion I have for you is if you don't have data you need on that disk just use gparted to delete all the partions on it, including that extended one until it shows just unpartioned space and create a brand new partition of your choice.  I was in a similiar situation as you and no solution worked aside from just completely starting over with the disk. Now mine works fine and I don't have any mount issues. 

I think what's happeneing is somewhere along the lines the disk label and the information about the file systems is getting corruped.  Mine used to be an external NTFS drive which worked fine and mounted great when I used it as an external USB hardrive.  Then I decided to install it in the computer physically and all of a sudden fdisk was telling me it was ext3 and the disk utility was telling me it was NTFS.  Unable to mount it.  It sucks but if you  don't need the data or can get it off somehow else just start over.  Sorry.

---

