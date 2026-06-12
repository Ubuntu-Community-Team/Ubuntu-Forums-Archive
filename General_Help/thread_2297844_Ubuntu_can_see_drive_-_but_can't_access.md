---
title: "Ubuntu can see drive - but can't access"
date: 2015-10-07
forum: General Help
---

### Post by GoBears2011 on 2015-10-07
Greetings....

I have a Seagate BlackArmor 110 NAS 2 TB drive that died.  I figured it was the network card b/c it didn't make any funny noises and the lights on the network connection never went to green. I pulled the drive out and put it in an external case hoping to recover the data.  Windows can't access it. My goal is to recover the files to another disk.

This is actually deja vu....I had this problem several years ago also with another drive ([here]("http://ubuntuforums.org/showthread.php?t=1669898")).  Since then I've been using Ubuntu on a laptop connected to my PC for casual surfing, online content, etc.

Back to the present...hoping it's Ubuntu to the rescue again. I found my old post and gave it a try....doesn't work.  Need some help here.

The drive shows up the File Browser as "Array".

In Disk Utility it shows up both as Peripheral Device (connected via USB) as a 2.0 TB Hard Disk.  All the information displayed is encouraging.  It also shows up under Local Storage as "Multi-disk Devices" then "Array....which jives with the File Browser but under Volumes it says "Raid Array is not running".

Here is the partition info I was able to get from the command window using the parted -l command:

Model: ST320005 42AS (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system     Name  Flags
 1      100MB   1169MB  1069MB  ext3                  raid
 2      1169MB  2239MB  1070MB  linux-swap(v1)        raid
 3      2239MB  2773MB  534MB   ext3                  raid
 4      2773MB  2000GB  1998GB  ext3                  raid




Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.


I tried the tricks I did before...no luck.  I tried a bunch of things from searching the forum but can't find the same scenario and they haven't worked.  Probably an odd one as I pulled the NAS drive and stuck in into an case and it's now connected via USB.  Any ideas?

Thanks,

Dave (noob)
[ATTACH=CONFIG]264841[/ATTACH][ATTACH=CONFIG]264842[/ATTACH][ATTACH=CONFIG]264843[/ATTACH]

---

### Post by GoBears2011 on 2015-10-07
I found this article -

[https://www.synology.com/en-us/knowledgebase/faq/579](https://www.synology.com/en-us/knowledgebase/faq/579)

My dead NAS wasn't a Synology but it sounded similar.  I went through the steps installing mdadm and lvm2 then running mdadm:

user@T43:~$ mdadm -Asf && vgchange -ay
mdadm: failed to create /dev/md1
mdadm: failed to create /dev/md2
mdadm: failed to create /dev/md3



Didn't work but something did change. Now in the file browser the disk doesn't show up at all and only shows up as a peripheral device in Disk Utility.  Still can't access the drive.  Not sure if this is a step forward or back.

---

