---
title: "Creating Partitions"
date: 2008-06-10
forum: General Help
---

### Post by +Eric on 2008-06-10
I'm relatively new to linux and need some help with partitioning. I am pretty well versed with windows and how to handle partitions there, but not so much with linux. I originally installed linux on my laptop inside windows (using wubi I guess?), but now it's time to get thing done a bit better.

I installed windows first as I still need it :(. I partitioned the 60 gb drive giving windows 20, and leaving aprox 30 unpartitioned. 2 gigs are taken up for what I think is the dell utillity partition, and 3gig for MediaDirect, and I don't wanna lose that (well, mediadirect anyway).

There are currently 4 partitions when I create one for Windows. One is fat16, possibly Dell Utility partition? One is 2gb, one is 3gb, and 20 for Windows. I have no idea what the two 2 that are 2 and 3gb are, although I'd assume one is for MediaDirect. it's sort of confusing really, because only 1 partition shows up in windows (the actual windows partition)........

I have inside 8.04 install:
/dev/sda
 /dev/sda1  fat16
 /dev/sda2 ntfs     
 free space - for linux! 30gb....
 /dev/sda5 fat32
 /dev/sda4 fat32
 unusable

So I can used guided - "Guided - use the largest continous free space", or should I use Manual. Will the guided option use the unpartitioned space? Are there any other things I should be worried about?

I would just test and if things didnt' work out like I wanted, start again. But I would like to keep mediadirect (for no great reason, however I do use it to watch movies).

---

### Post by anystupidname on 2008-06-10
Try one of these liveCDs/liveUSBs;

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.ScreenShots](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.ScreenShots)
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

or even easier, gparted via unetbootin:
[http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127)

all nice n GUI for ya... :-)

---

### Post by +Eric on 2008-06-10
I'd really just like to do it in the ubuntu installer.....

---

### Post by JC Cheloven on 2008-06-10
Let's see what you have exactly. Please from the live cd open a terminal and execute
```
sudo fdisk -l

```
And post the output of that

---

### Post by +Eric on 2008-06-10
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        2556    20482875    7  HPFS/NTFS
/dev/sda3            6595        6855     2096482+   f  W95 Ext'd (LBA)
/dev/sda4            6856        7295     3534300   db  CP/M / CTOS / ...
/dev/sda5            6595        6855     2096451   dd  Unknown

Disk /dev/sdb: 4127 MB, 4127195136 bytes
16 heads, 32 sectors/track, 15744 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15744     4030448    c  W95 FAT32 (LBA)
```

---

### Post by JC Cheloven on 2008-06-10
Well I see what you have. It is important to see that you have already an extended partition (sda3), which is necessary, as you will create two more partitions. I see that you have a second drive of about 4GB, which I suppose is a pendrive or something like that.

--> I think it's safe to proceed with the 'Guided - use the largest continous free space'. 
-->But I'd suggest to make the partitions first, with gparted from the live cd, and then installing ubuntu choosing "manual partitioning". This gives me more feeling of control.

In both cases, the goal is to end up with two partitions: one formatted in ext3 with mountpoint "/" of about 28GB, and one formmated as swap, of about 2 GB. (The amount of swap at least the size of your ram). Both in the extended partition you already have.

If you find your way around with this, great. If not, come back to ask. I'll be back in few hours.
Greetings

---

### Post by +Eric on 2008-06-11
Cool, thanks! Got it worked out!

I ran:

```
sudo apt-get install gparted
```

after booting up the live cd, partitioned the drive with it, then ran the installer.... easy!!! Gparted is an easy little tool!

Thanks again guys!

---

### Post by JC Cheloven on 2008-06-11
Congratulations! Enjoy your new OS ;-)
Only: it wasn't necessary to install gparted, as it comes preinstalled in the live cd. You could have run it out of the box.
Greetings

---

### Post by +Eric on 2008-06-11
Hmm, I tried running "gparted" from the command line and I believe and it didn't run.

Although I can't specifically remember if I tried it on my desktop (also 8.04) or on my laptop with the live cd in.

Either way, I got there! :-)

---

