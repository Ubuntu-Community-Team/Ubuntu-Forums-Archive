---
title: "Hard Drive Problems"
date: 2007-05-22
forum: General Help
---

### Post by a1tone on 2007-05-22
Hello,

I have just installed Linux. My PC has two hard drive. One is 6.4GB, which is where I have Linux installed and the other is a 40GB.

Two problems the 40GB dosen't appear to show in Ubuntu, but it does show when I do fdisk. But when I do fdisk the 6.4 GB show fine, but the 40GB shows as a 57.2GB???

Also it says on the second hard drive 4 partitions, but I haven't set any of them and Partitions 2,3 and 4 don't end on cylinder boundary.

So the questions really are:

Where is the drive in Ubuntu?
Where has the extra space come from?
Can I delete these partitions? If yes, How?
Will this cure the partitions not ending on a cyclinder boundary. I guess they would if they aren't there.

Been using Windows for many years and just trying to get my head around Ubuntu.

Thanks in advance for any help!!!

---

### Post by Soybean on 2007-05-22
What is on the 40Gb drive? Is it a Windows drive that was set up by Dell or some other computer company? They often put a few hidden partitions on your hard drive for system recovery or diagnostic tools.

You can definitely delete the partitions, but personally, I'd want to find out what they were first. ;)

Why not paste the output from ```
sudo fdisk -l /dev/hda
``` here? Someone can probably make some sense out of it. :) Of course, replace "/dev/hda" with the device for the mysterious hard drive.

As for where it is in Ubuntu... it may actually depend on what's on it. I think Ubuntu should have set up mount points for the partitions under /media during installation, but if it didn't recognize the file system(s), it might not have.

---

### Post by a1tone on 2007-05-22
The drive was brought from Ebay, so what is on it I don't really think is that important. Nothing that I will need anyway.

The following is displayed when entering sudo fdisk - l /dev/sdb

Disk /dev/sdb: 57.2 GB, 57200795648 bytes
251 heads, 63 sectors/track, 7065 cylinders
Units = cyclinders of 15813 * 512 = 8096256 bytes

Device  Boot          Start          End          Blocks          Id     System
/dev/sdb1               2122        4943     22301121        c      W95 FAT32  (LBA) 
/dev/sdb2               2122        4244     16777472        0      Empty
Partition 2 does not end on cylinder boundary.
/dev/sdb3               2122        4244     16777472        0      Empty
Partition 3 does not end on cylinder boundary.
/dev/sdb4               2122        4244     16777472        0      Empty
Partition 4 does not end on cylinder boundary.

---

### Post by LaRoza on 2007-05-22
Since this is a used drive, I would wipe it completely before using it. I do not know what kind of drive it is.

I would suggest using GParted to completely reformat the entire drive. That way you know exactly what is on it.

---

### Post by a1tone on 2007-05-22
The drive is an internal Drive. Western Digital 40GB IDE Hard Drive.

---

### Post by LaRoza on 2007-05-22
I would still do it (wipe and reformat).

---

### Post by a1tone on 2007-05-22
Will do, Thanks for your help.

---

