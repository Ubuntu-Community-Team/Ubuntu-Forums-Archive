---
title: "Help, I (think) that I installed ubuntu over my windows 8 partitions"
date: 2013-11-23
forum: General Help
---

### Post by sofian2 on 2013-11-23
Hello

First, sorry for my english, it isn't my mother tongue.

My problem is, I wanted to reinstall ubuntu (13.10) and I chose to do it over mine old 13.10 ubuntu because I had some problems. 
Now I can't boot windows or find it in the boot menu. And ubuntu has all mine partitions of mine pc. 
Could I recover windows? Or at least recover the files I had on windows? 

Thank you!

---

### Post by J_Me on 2013-11-23
From a terminal run 'sudo fdisk -l' without the quotes and post back here the output

---

### Post by sofian2 on 2013-11-23
sofian@sofian-HP-Pavilion-g6-Notebook-PC:~$ sudo fdisk -l
[sudo] password for sofian: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd7f0f8f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

---

### Post by sofian2 on 2013-11-23
This is what I got

---

### Post by philinux on 2013-11-23
> **sofian2 said:**
> This is what I got

If you search that error message it gives a few hits, one of which is this. [http://ubuntuforums.org/showthread.php?t=1952953](http://ubuntuforums.org/showthread.php?t=1952953)

I'm still on old stuff with win 7 so I have no knowledge of this but someone else may be along to help.

I wouldnt do anything unitl you get some good advice.

---

### Post by sofian2 on 2013-11-23
Ok, thanks! :)

---

### Post by mastablasta on 2013-11-23
boot form live ubuntu disk and run gparted. i htink you may need to install it first and then take a screenshot and post it here. that should show the partition layout. another option might be to run bootinfo script and then post the result here iusign code tags (#)

---

### Post by sofian2 on 2013-11-24
Gparted screenshot: [http://i.imgur.com/rICXvah.png](http://i.imgur.com/rICXvah.png)

---

### Post by Mark Phelps on 2013-11-24
> Could I recover windows? Or at least recover the files I had on windows? 

The (former) Windows partition(s) is/are gone.  You might be able to restore the former partitions if you download and burn a CD from the free Minitool Partition Wizard Boot CD ISO file.  That is a Windows filesystem partitioning tool which might be able to recover the former partitions.

---

