---
title: "Finding Command that Automounts Slave Hard Drives"
date: 2015-10-12
forum: General Help
---

### Post by chiques on 2015-10-12
Does Ubuntu keep a record of what command is ran when mounting a hard drive in the desktop environment?

Reason being: I have a hard drive that is paritioned somewhat strangly (see below). I was trying to mount it on a seperate workstation and I could not figure out how to do it. I plug it back into the native machine and it mounts right away. I'd like to study the "> mount -option -whatever" that ubuntu uses to automount it when I click on the icon.

Here is what the fdisk -l output looks like:

```
Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x3dc8657e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3961709324  1980854631    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sdb2      3961709325  1565560768   949409370    7  HPFS/NTFS/exFAT
Partition 2 does not start on physical sector boundary.
Note: sector size is 4096 (not 512)
```

As you can see it is not clear what format was used on these drives.

Thanks for any guidance.

---

### Post by Morbius1 on 2015-10-12
> I'd like to study the "                                                         mount -option -whatever                      
     
 
" that ubuntu uses to automount it when I click on the icon.
It doesn't use a "mount -option -whatever.

When the system detects that something new has been added or when some partition is present that is not defined in fstab it alerts udisk2 that "there be something new here".

When you click on the icon it runs:
```
udisksctl mount -b /dev/disk/by-uuid/bunch-of-numbers
```
A temporary mount point is created at /media/$USER/LABEL if there is a LABEL or /media/$USER/UUID if it has no LABEL.
> As you can see it is not clear what format was used on these drives.
It's only fdisk that's confused. Run this command instead:
```
sudo blkid -c /dev/null
```

---

