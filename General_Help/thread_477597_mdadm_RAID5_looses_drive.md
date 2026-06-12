---
title: "mdadm RAID5 looses drive"
date: 2007-06-18
forum: General Help
---

### Post by Cellojazz on 2007-06-18
Hi all,

I've created a RAID 5 array with an LVM on top of 1 GB over 3 500GB drives.  When I hard power off (to test)l, it looses the 3rd drive (sdd).  I think its because I added a new sata drive recently, and instead of giving it a lesser drive letter it gave it an earlier drive letter.   (sda vs. sdd and shifted all the other drvies down 1)

I changed the config on mdadm.conf so instead of
 
```

ARRAY /dev/md0 level=raid5 num-devices = 3 UUID= {big-uuid}
     devices = /dev/sda1,/dev/sdb1,/dev/sdc1
```

it now reads

```

ARRAY /dev/md0 level=raid5 num-devices = 3 UUID= {big-uuid}
     devices = /dev/sdb1,/dev/sdc1,/dev/sdd1
```

Question 1 - are there any other config files I need to check to get this working better?

I would assume that it would still allow the raid to be started, just not clean, and continue to clean it while the os is running.  As it is now, I have to boot to my /home directory on the boot disk, and rebuild it, then reboot to bring back my array as /home (which is what I use it primarily for).

Question 2 -
Is this normal behavior, because as thunderstorms can kill power around here more frequently than in some places, I can't have it take an hour to rebuild an array every time the server hard shuts down.  

Any help would be greatly appreciated.  If it continues to be a problem, this may kill my efforts of moving Linux into my office.

Thanks!

---

