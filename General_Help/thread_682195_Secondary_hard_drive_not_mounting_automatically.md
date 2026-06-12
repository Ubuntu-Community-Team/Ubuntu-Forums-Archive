---
title: "Secondary hard drive not mounting automatically"
date: 2008-01-29
forum: General Help
---

### Post by stdPikachu on 2008-01-29
My myth system has a secondary hard drive in it, with a couple of NFS mount points hanging off it. But when the system boots, it isn't mounted and I have to run a subsequent `mount -a` to get things running. Have tried device node and UUID entries in fstab to no avail;
```
banquo@banquo:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9a486baf-5cd3-48d0-ad3a-34e8ad100467 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=80ae49ba-1d8d-43f1-bc99-83bfb9ee94c6 none            swap    sw              0       0
# /dev/sdb1
#UUID=f4ab299d-6575-41e4-a4df-c54678b909df /storage     jfs     defaults,noexec 0       0
/dev/sdb1                                /storage       jfs     defaults,noexec 0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

# nfs mounts
prospero:/storage/movies        /storage/movies nfs     ro,hard,intr,bg,rsize=8192,wsize=8192   0 0
prospero:/storage/tv            /storage/tv     nfs     ro,hard,intr,bg,rsize=8192,wsize=8192   0 0
```
There's nothing obvious in dmesg or /var/log/*... any ideas?

---

### Post by c0mp13371331337 on 2008-01-29
Hmmm, that's a good one.  I was going to suggest fstab, after just reading the subject.... but yeah, seems like you've about got that covered.  All I needed to do was to add the entry to fstab to get my second harddrive to mount automatically with the rest of the system, so I'm not sure what's going on there.  Best of luck though!

---

### Post by dcstar on 2008-01-30
> **stdPikachu said:**
> My myth system has a secondary hard drive in it, with a couple of NFS mount points hanging off it. But when the system boots, it isn't mounted and I have to run a subsequent `mount -a` to get things running. Have tried device node and UUID entries in fstab to no avail;
.........

Install the** pysdm** package and then use System-Administration-Storage Device Manager to set up the mount.

---

### Post by stdPikachu on 2008-01-30
What does pysdm do that editing fstab doesn't? I'm not much of a GUI person.

---

