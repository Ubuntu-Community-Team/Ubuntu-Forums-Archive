---
title: "Recovering Data from a hard drive"
date: 2013-03-14
forum: General Help
---

### Post by Greyoregano on 2013-03-14
First let me provide a bit of a back story. A few years ago I bought a D-Link DNS-323 NAS so that my wife and I could keep our photos and important digital media safe (ran it as RAID 1). The last few years it has been giving us problems. I always wanted to fool around with Ubuntu/Linux and finally found the time. I set up a basic server with some help, and it finally came time to transfer the files. Turns out the one disk is dead, can't get any info off of it. 

The second one is working, but it will not let me access it. I tried to use the hard drive in the DNS-323 networked, but it won't let me access it (permission denied). Used the DNS-323 ftp server, and with that I was able to access it and see the files but I couldn't download anything. Unplugged the hard drive and plugged it into my Windows machine (used a program that will read ext2/ext3 formatted disks) and it would not let me in. Finally I plugged it into my Ubuntu machine and did a *fdisk -l*, and it told me the partition was invalid.

Please! does anyone know how I can get the files off of the hard drive (or point me in the right direction), my wife and I have (the first) six years of pictures of the kids on it. I thought I was doing the safe thing in running it in RAID 1, but alas it's not fool proof.

Thanks for any help

---

### Post by the_funtom on 2013-03-14
Hi

I currently have the same problem with my external hard disk 1.5 TB....couldn't access the hard disk at all in windows and then decided to explore how I could retrieve the data. I installed testdisk ([http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)), and finally could access the hard drive at least in ubuntu but still am trying to figure out how i can do so in windows (vista). I'm sure testdisk should be able to help. Run this on ubuntu cos in windows this doesn't work that great. And its far easier to access data in ubuntu than it is in windows.

(Only if you still can't access the data in windows) If you have another hard disk in hand, then I'd suggest copying all your data (at least the important ones) and then reformat your hard disk (the problematic one) and restore the data back to the hard disk.

Best of luck. I hope I'm able to figure out what to do with mine.

---

### Post by zero2xiii on 2013-03-14
Hay,

+1 for testdisk:
```
sudo apt-get install testdisk
```

This program is relatively easy to use. Just follow the on screen instructions.
A quick run through of some of the strange things noted: (note this might differ from system to system)
```
sudo testdisk
#create new log
#arrow keys select faulty drive
#proceed (enter key)
#Intel Partition
#proceed (enter Key)
#analyze
#proceed (enter key)

```
Now from here the steps will start to vary. A quick search should lead to a new list. Just follow the on screen instructions carefully.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
There you will find a rather in depth guide with multiple scenarios and cases. Read through there and hopefully you will see the light.

Rebuilding a raid can be rather hard. So don't try that just yet. However RAID1 is just a clone of drive 1 to drive 2. So you might actually use that to your advantage if your data is that critical for recovery, but that is a rather tedious procedure and requires a LOT of space to work. Usually: Original_drive_capacity x 3

Good luck

EDIT:
Here is a nice step by step, although for NTFS partitions, the procedure for ext2/3 is almost identical.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by montgomeryj on 2013-03-14
A great tool used for forensic recover of data off of hard drives is Autopsy which utilizes sleuthkit.  You can find download, installation and user information at [http://www.sleuthkit.org/autopsy/download.php](http://www.sleuthkit.org/autopsy/download.php)

There are also some great tutorials and walk-throughs on how to use this tool, both on that website and on various forums.  Just use a little bit of Google and you'll find the help that you to use this tool and recover those picture.

---

