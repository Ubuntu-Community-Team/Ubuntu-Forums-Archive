---
title: "Ext2/Ext3 Question"
date: 2007-11-03
forum: General Help
---

### Post by Sliver X on 2007-11-03
I recently ditched the last of my FAT32 partitions in favor of an all Ext* solution. However, I have a question that hours of Google-Fu hasn't been able to answer for me...

I used tunefs to disable the scheduled fsck checks that happen after so many mounts/days, because I have over half a TB of data across my drives and this takes eons to finish (And I shut my machine down every night, so leaving it on all the time is *not* an option for me).

My question is that since this is disabled, will the OS do a fsck if the drives aren't unmounted cleanly? This is really the only time I would want the system to check the file system integrity. I edited fstab in the hope of making this the default behavior, as shown here:

proc            /proc           proc    defaults        0       0

/dev/sda2	 /               ext3    defaults,errors=remount-ro 0       1

/dev/sdc1	 /home           ext3    defaults,errors=remount-ro 0       1

/dev/sda1	 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

/dev/sda3	 /media/sda3     ext3    defaults,errors=remount-ro 0       1

/dev/sdb1	 /media/sdb1     ext2    defaults,errors=remount-ro 0       1

/dev/sda4	 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Any help is greatly appreciated!

---

### Post by der_joachim on 2007-11-04
Dirty unmounts should always automatically trigger a disk check. AFAIK that's default behaviour for most modern file systems.

---

