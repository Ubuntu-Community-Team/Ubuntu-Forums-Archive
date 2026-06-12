---
title: "dd'ed to the wrong drive. Please help with recovery"
date: 2014-03-16
forum: General Help
---

### Post by nstgc379 on 2014-03-16
Both fdisk -l and gparted said that /dev/sdb were for a USB drive which I was copying an ISO onto via # dd if={the iso} of=/dev/sdb

Well, they were both wrong. Everything should still be there, but the drive MBR is trashed, as will be the first few megabytes of the first partition.

The first partition is my WIndows partition, and doesn't really have anything too important on it. The second is an EXT 4 partition with my regular back ups on it. In additoon to that, I have a nasty habit of sometimes deleting stuff that has been back up so in reality its the only copy.

HELP!

---

### Post by buzzingrobot on 2014-03-16
Can't offer any recovery help, but I've done the same thing when another USB drive was already mounted on /dev/sdc.  I attached a USB stick and assumed it be mounted on /dev/sdd. So, I burned the image to /dev/sdd.

Turns out the mounts moved when I attached the USB stick. It was mounted on /dev/sdc and the drive moved to /dev/sdd. I wiped out a 1TB backup drive.

---

### Post by oldfred on 2014-03-16
The ISO also does not use standard partition table.
Do you know sizes, and start locations in  sectors of your partitions? Ideal would be backup of partition table, or printout of fdisk or parted with sector detail.

You can try testdisk. You may have to dd zero out the partition table as the ISO may make a new fdisk or parted show very strange results like it has random data which from ISO it is.

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

sudo parted -l
sudo fdisk -lu
      
 Zero out MBR and partition table:
dd if=/dev/zero of=/dev/sdX bs=512 count=1

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by nstgc379 on 2014-03-16
I unfortunetely don't know where the sectors started. One of them started imediately after the MBR (or so I suspect), but I don't know which. I'm hoping that its my Windows partition since it was only for gaming, and doesn't have anything important, but I suspect that, unless I screwed up, my linux partition was first.

A friend of mine suggested that I use [http://www.youtube.com/watch?v=MkErvUsRQIA](http://www.youtube.com/watch?v=MkErvUsRQIA), which I will try sometime today after I get a new linux installation going on another disk. I think I'll try test disk first since it looks less likely to cause mroe damage.

---

### Post by oldfred on 2014-03-16
Typical install starts at sector 2048. Unless older, then sector 63.
Windows also has a small 100MB boot partition and then the main install. But the ISO is large enough to have overwritten the beginning of the main install also. Most normal installs do have Windows first, but if you manually installed it may not be.

---

### Post by nstgc379 on 2014-03-16
Yeah, its a newer one, and it was manual. Since Windows tends to be slower than Linux, and becasue I tend to forget that HDDs read from the outside inward, I put the Windows at the end of the drive typically. Also, that 100MB partition you are refering to is on a different drive. There is no cushion. I'm just going to have to hope that TestDisk can recover as much as possible. Failing that I'll try my friends method.

---

