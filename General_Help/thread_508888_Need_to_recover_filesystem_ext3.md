---
title: "Need to recover filesystem ext3"
date: 2007-07-24
forum: General Help
---

### Post by dnt4getdawld on 2007-07-24
I am relatively new to Linux. I recently (7/20/2007) agreed to help a man whose machine had died. He decided to give up on the machine, but asked if I recover some pictures. I attempted to do so by attaching his drive to my machine. (His was XP installed NTFS file system). After attaching his drive I restarted my machine. Upon doing so GDM failed to start. The machine then appeared to become unresponsive. I quickly gave up on recovering his pictures. I shutdown the machine and removed his drive.

This is when I start getting into trouble. When I restarted my machine it told me that the GRUB failed because of error 17. I restarted it in hopes that it would magically fix itself. This time it told me the GRUB failed because of error 18. I began to panic because I have in excess of 1000 irreplacable images. It is my fault that I neglected to create a backup. In fear of losing those images I detached the drive and installed a new one. 

After installing a new drive (identical in every way except for the data on the drive) I reattached the original drive. Both drives are 250 GB Samsung IDE drives. Ubuntu now recognizes both drives as SCSI and has titled them sda1 and sdb1. sdb1 is the drive with the pictures on it. I attempted to mount the drive, but it failed because the file system was not ext3. This confused me because I new that I had installed it as ext3. I then installed GParted to make sure that the file system was in fact not ext3. GParted reported the file system to be unknown.

This is where I have no idea what to do next. So I came here. I need your help. I need to recover those photos. Nothing else on the drive matters. Those are pictures of my son being born. Those are the first thousand pictures of him. He is three months old (I know I take a lot of pictures) and I will not have another chance to see those images again without those photos. Someone please help...

---

### Post by bodhi.zazen on 2007-07-24
See if these links help : 

General : [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) (needs work)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) #Testdisk is in the Ubuntu repositories

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by dnt4getdawld on 2007-07-25
Thank you I will be reading all of those when I get home from work. Hopefully you will have just saved me. Thank you again.

---

