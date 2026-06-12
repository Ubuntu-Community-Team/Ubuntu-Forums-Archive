---
title: "Adding another HD, mounts in place of existing drive?"
date: 2007-01-20
forum: General Help
---

### Post by NT4usB on 2007-01-20
I bought a bigger drive to use for storing MythTV recordings.
I plug it in to the third SATA spot on the board, thinking I'll format & copy the existing recordings over.
When I boot, the new drive shows up as sdb and bumps the existing sdb drive to sdc.
Now I can't see the files on the 'real' sdb and am really nervous about formatting the 'sdb' that shows up empty for fear of wacking the real sdb.
Tried umount sdb, sdc, sdb1, sdc2, etc. not found.

Unplug the new drive, reboot, and all is well...

How do I plug in the third drive and get it to take it's place in line as sdc?
I've heard SATA are hot swappable but I don't think that's the answer... *g*

Current fstab:```
sh-3.1$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump> <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0      1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/sda3       /media/cache/mythtv     ext3    defaults        0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/fat32    vfat    users,umask=0,auto      0 0
/dev/sdb2       /media/lib/mythtv       ext3    defaults        0 0
sh-3.1$ 
```

---

### Post by bodhi.zazen on 2007-01-21
Well, I think you may want to mount by label or uuid rather then /dev/sdxy ....

But ....

Try this:

Change you fstab to:

>  
/dev/sdb1  /media/new_drive auto defaults  0 0
/dev/sdc1       /media/fat32    vfat    users,umask=0,auto      0 0
/dev/sdc2       /media/lib/mythtv       ext3    defaults        0 0

Then:```
sudo mkdir /media/new_drive
```

The re-boot and see what is mounted where ;)

To use uuid or LABEL in FSTAB:

UUID=xx-yyy-zzz /mount_point ........

LABEL=XXX /mount_point ......

To list your partitions by uuid or label:

```
ls /dev/disk/by-uuid -l
ls -l /dev/disk/by-label
```

See also here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

HTH

---

### Post by NT4usB on 2007-01-21
Thanks for the tips and fstab link. I'll save that for future reference.

I was pressed for time (had to record House at 11:00 *g*) so I swapped cables around and got the drives in the right holes. 
Renamed the existing .../mythtv. Mounted the new drive to .../mythtv. Copied ~150 GB in a little over an hour (while recording House to it, and changing ownership, and permissions, all at the same time... gotta love Linux)
Soon as I could shut down, I put it all back together and edited fstab since I only have sdb1 now.
Have room for ~350 hours of programs now. Too bad football season's almost over...

---

