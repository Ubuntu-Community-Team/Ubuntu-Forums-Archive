---
title: "gdisk not writing UUIDs - any way to specify UUID for hfsplus (either MBR or GPT?)"
date: 2015-05-05
forum: General Help
---

### Post by David_Madison on 2015-05-05
I have an external HD that I am setting up for backups.  I want to use the same UUIDs as my other backup drive so I can mount them in the same place using UUID on fstab (it would be great if we could specify different UUIDs to the same mount point and have it figure out which one is available, but that's another post).

I have ext4 and an hfsplus partition on these drives.

I tried using gdisk to create a partition but was stymied when I tried to format the hfsplus because it wasn't aligned to 4k, and I couldn't figure out how many sectors would accomplish that.  So I used gparted to create the hfsplus partition, then reopened in gdisk to set the UUID using the 'c' command from the 'x' expert menu.

Unfortunately it did nothing, I would write the partition table afterwards and run 'blkid' and see that gparted completely failed to change the UUIDs (though it could create partitions just fine).

So I switched to MBR using fdisk, and managed to change the UUIDs with 'tune2fs -U' but there is no such hfsplus tool.  So the hfsplus has the wrong UUID.

How can I fix this, either with MBR or GPT??

---

### Post by bab1 on 2015-05-05
> **David_Madison said:**
> I have an external HD that I am setting up for backups.  I want to use the same UUIDs as my other backup drive so I can mount them in the same place using UUID on fstab (it would be great if we could specify different UUIDs to the same mount point and have it figure out which one is available, but that's another post).

I have ext4 and an hfsplus partition on these drives.

I tried using gdisk to create a partition but was stymied when I tried to format the hfsplus because it wasn't aligned to 4k, and I couldn't figure out how many sectors would accomplish that.  So I used gparted to create the hfsplus partition, then reopened in gdisk to set the UUID using the 'c' command from the 'x' expert menu.

Unfortunately it did nothing, I would write the partition table afterwards and run 'blkid' and see that gparted completely failed to change the UUIDs (though it could create partitions just fine).

So I switched to MBR using fdisk, and managed to change the UUIDs with 'tune2fs -U' but there is no such hfsplus tool.  So the hfsplus has the wrong UUID.

How can I fix this, either with MBR or GPT??
Whichever formatting you use, it is possible to mount a partition by its partition label (e.g LABEL=MYBACKUP) instead to using UUID.  The mount command will accept the /dev or UUID or LABEL as the partition ID.  

You do realize that you can only have one working partition mounted at any mount point at any one time.  If you mount a partition where another partition is already mounted you will only have access to the last partition mounted.  The last mount will hide the previously mounted partition.

---

### Post by Holger_Gehrke on 2015-05-05
UUID are meant to be **u**niversally **u**nique **id**entification. Give labels or names to the partitions instead (e2label for ext[234], don't know about hfs); if a partition has a label it is used as the name for the mount point.

---

