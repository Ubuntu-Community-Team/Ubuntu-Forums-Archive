---
title: "System monitor mountpoints?"
date: 2007-07-26
forum: General Help
---

### Post by Nem1976 on 2007-07-26
This moring I rebooted and apparently I had some issues with bad blocks on my Hard drive.  Once the fsck finished checking the drive and repairing I was able to get back into gnome.  But things weren't working properly.  Emerald themes weren't working as well as my screenlets.  I went into system Monitor and looked at the Filesystem tab and found this See attachment.

I looked at another ubuntu box almost identical to mine and it doesn't look anything like this it only has /dev/sda2 mounted. 

Any help would be great.  

Thanks

---

### Post by tronica on 2007-07-26
The first thing that comes to mind is your fstab is messed up, post your /etc/fstab.

---

### Post by Nem1976 on 2007-07-26
Here is my fstab.  Everything looks fine under this. 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eab970e8-7ba9-4f5d-a4ce-c48598bb06f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=9d9c2aac-e02e-48a7-b17f-5e45d7672d25 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/sdb1 	/media/40gig	 ext3	 defaults, 0 0
```

---

### Post by chrisccoulson on 2007-07-26
Your screenshot looks normal to me. The extra mountpoints you see are because you have 'Show all filesystems' checked in the preferences dialog for System Monitor. If you uncheck that, you will only see /dev/sda1 and /dev/sdb1.

---

