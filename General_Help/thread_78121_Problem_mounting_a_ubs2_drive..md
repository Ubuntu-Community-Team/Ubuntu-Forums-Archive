---
title: "Problem mounting a ubs2 drive."
date: 2005-10-17
forum: General Help
---

### Post by BIGtrouble77 on 2005-10-17
I can't get my 300gb fat32 usb2 drive to mount anymore.  It has been working fine for quite a while.  My other drives mount fine in ubuntu.  This drive mounts perfectly fine on my windows machine.  

GParted says that's it's "unable to read some contents of this filesystem.  Because of this some operations may be unavailable".  Could my winxp machine have done something evil to the file system??? If it did, i'd love to go shove this thing up bill gates' ass. :mad: 

Any help would be greatly appreciated.  I know I could copy everything off and reformat it, but I'd much rather get some info so I can avoid this in the future.

Thanks,
-BT

---

### Post by darknuala on 2005-11-16
Try reformatting your usb drive in windows, then try copying something to it in linux.  I had that happen before, and a reformat fixed it.

---

### Post by aysiu on 2005-11-16
How were you mounting it before? Can you plug it in and post the output of these two commands? ```
sudo fdisk -l
``` ```
cat /etc/fstab
```

---

### Post by BIGtrouble77 on 2006-01-06
Here's the output.  Sorry I took so long to reply, I had to take my system down for a while.  

The 300gb device is the external drive.  I can mount it, but I'd like it to automount like every other drive.  I think winxp modified the drive for some reason.  I had to format it in ubuntu to get the whole 300gb in fat32.

```

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12161    97683201    7  HPFS/NTFS

Disk /dev/hdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       11665    93699081   83  Linux
/dev/hdb2           11666       12161     3984120    5  Extended
/dev/hdb5           11666       12161     3984088+  82  Linux swap / Solaris

Disk /dev/sda: 2048 MB, 2048901120 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         992     1999840+   6  FAT16

Disk /dev/sde: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       36481   293033601    6  FAT16
bob@bobbyhotep:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by plors on 2006-01-06
did you install the dosfstools? gparted needs them to obtain the used and unused space on a filesystem.

---

### Post by BIGtrouble77 on 2006-01-06
[QUOTE=plors]did you install the dosfstools? gparted needs them to obtain the used and unused space on a filesystem.[/QUOTE]
dosfstools is installed by default.  

I can mout the drive this way:
sudo mount /dev/sde1 /media/usbdisk

SDE shows up as a fat32 device in gparted. 

I just don't understand why it won't automount.  Do I have to create a special mount point for it?  usbdisk is my cf card mount point.

---

