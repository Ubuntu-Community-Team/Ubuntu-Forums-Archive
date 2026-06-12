---
title: "best file system and root size"
date: 2007-11-13
forum: General Help
---

### Post by malfist on 2007-11-13
My upgrade to gusty finally crapped out on me and I can't do anything to it, it won't connect to ethernet, it doesn't like the nvidia driver, it locks hard when I click the shutdown button on menu or panel (Have to do SysRq and busier). I'm giving up on it. I've backed up my /home/jerome/* and am going to do a total reinstall of gusy, if this doesn't fix it, I'm going back a version or to fendora.

Anyways, my question to you is, this time I am dividing the root and home directories. How can I set ubuntu to do that, and how large should the root partition be?

Also, is ext3 the best file system or should I go with another?

Thanks,
Malfist

---

### Post by anaconda on 2007-11-13
for ubuntu ext3 is the best, because it is well supported, has recovery tools and it is also accessible from windows. (with is-drivers)

And the size of the root partition:
 I am afraid that many people will answer to that with the minimum recommended size, which is correct if you have a small hd, but if you have plenty of space you should make it as big as 20GB.. 10GB is also a good size, but it CAN become full if you install lots of programs and dont keep it clean.. eg. empty roots trash, clean apt-cache etc.

Also some programs (games) can be 4GB, and they might want to install to root partition, and I think eg. VMWares virtual disks are installed to root partition by default??? They can also be quite big, but can as well be installed to home,,

So if you have plenty of hd space make / 20GB
if hd space is a problem 10GB is good too

---

### Post by PmDematagoda on 2007-11-13
Ext3 is the most reliable though I've had good luck with JFS which is faster, so if you are aiming for reliability then go for ext3, but if you are aiming for a good mixture of speed and reliability then you can go for JFS.

And the size could be about 10Gb for the /(Root) partition and the remainder for the Home partition.

The partitioning can be done in the Ubuntu installation itself by selecting Manual in the partition and then setting the partitions according to the way you want.

---

### Post by malfist on 2007-11-13
I was looking through some benchmarking of the filesystems from about 2 years ago and ext3 and ext2 are really slow. JFS has some problems with large files, and I manage a few large files (iso, dvd's) but mainly it's small files (source code, music, documents, etc). Are there any more current benchmarks than the ones on: [http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)?

edit: I have a 200GB hard drive that is nearly full (~75%), so is 15GB good? (I've filled Mandriva's 8GB before, but I think that was because of a system update) Filling a partition isn't fun.

---

### Post by anaconda on 2007-11-13
> **malfist said:**
> I was looking through some benchmarking of the filesystems from about 2 years ago and ext3 and ext2 are really slow. JFS has some problems with large files, and I manage a few large files (iso, dvd's) but mainly it's small files (source code, music, documents, etc). Are there any more current benchmarks than the ones on: [http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)?

edit: I have a 200GB hard drive that is nearly full (~75%), so is 15GB good? (I've filled Mandriva's 8GB before, but I think that was because of a system update) Filling a partition isn't fun.

Yes. 15GB would be good. (many people recommend 10GB, but I have heard 10GB getting full.)

Wow.. I didn't know that ext3 would be that slow!! But I still prefer it because it propably has the best recovery tools and is accessible from windows.

---

### Post by malfist on 2007-11-14
I didn't think it would be either, after all, it is the default. Well, I've kinda given up with ubuntu on this run, I'm testing out gentoo, see if I like it. Would have been fendora, but it doesn't support JFS out of the box.

---

### Post by malfist on 2007-11-15
I'm loving JFS, I'm able to restore my /home from ubuntu onto my new gentoo installation, while compiling programs at the same time. JFS was the lowest for CPU usage, and only slightly slower than the other two (excluding ext2/3).

---

