---
title: "[SOLVED] Make new home directory"
date: 2008-01-07
forum: General Help
---

### Post by dondad on 2008-01-07
Right now, my home directory is a folder in the main partition. I have another partition that is 390 gig (sda3) that I want to use as home. I can back up all of the files in the current home, but how can I reset the extra partition to be my /home? here is fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71a54606-e1f8-4ffc-9394-bf1630ed12e2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=56ac47b0-967c-4acf-96a5-b2987db5646f /media/sda3     ext3    defaults        0       2
# /dev/sda2
UUID=0c690e52-8392-469c-a33f-b3a74496429b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

How can I get the files onto the new location, make it /home, and not mess up the permissions?

---

### Post by bodhi.zazen on 2008-01-07
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by dondad on 2008-01-08
I tried that, but when it was finished and I rebooted, I got an error that said that my home directory did not appear to exist. I looked, and the directory was there and the permissions seemed to be OK, but it would not boot.

In the process, I did end up with my home directory copied over to the new disk, so I reinstalled and set that as my home directory. That worked and fixed it, but I would like to know how to repair the original problem in case it happens again. The link assumes that you have hd0 etc., wheras I have sata drives and uuid's. I think that is probably part of the problem, but not sure how I should have corrected fstab to fix it. Any ideas?

---

### Post by bodhi.zazen on 2008-01-08
Yea, it sounds like you need to update fstab.

See if these two links help :

Basic partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

fstab : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by dondad on 2008-01-08
> **bodhi.zazen said:**
> Yea, it sounds like you need to update fstab.

See if these two links help :

Basic partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

fstab : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)


Thanks for the links. That will help me a lot in understanding what is going on. I got it working by the brure force method, but this could come in handy for the next time I hose the system ;-)

---

