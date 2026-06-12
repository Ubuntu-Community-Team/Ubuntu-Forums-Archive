---
title: "System not automounting a partition"
date: 2008-04-28
forum: General Help
---

### Post by pacsum on 2008-04-28
The system is not mounting a partition (sda2) at startup, what can I do?

---

### Post by ryanhaigh on 2008-04-28
Post your /etc/fstab, tell us what type of filesystem it is, check your system logs for related error messages.

---

### Post by pacsum on 2008-04-28
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7991d4eb-f3c2-4882-9111-1b1d3ce1c3eb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=df7516cb-f6a2-4b74-8d64-4af043cc79ad none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

VFAT

It should be sda2 but it's not even appearing :confused:

---

### Post by OmahaVike on 2008-04-28
yeah, i've had the same problem too.  i found a healthy discussion about it here in the closed hardy development forum:

[http://ubuntuforums.org/showthread.php?t=731401&highlight=fstab]("http://ubuntuforums.org/showthread.php?t=731401&highlight=fstab")

haven't tried it yet, so please don't blame me if it goes awry.

---

### Post by ryanhaigh on 2008-04-29
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

It doesn't mention the use of UUIDs but since you appear to only have on hard disk that shouldn't be an issue.

---

