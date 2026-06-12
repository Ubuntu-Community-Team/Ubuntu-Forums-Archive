---
title: "low on hard disk space?"
date: 2013-05-21
forum: General Help
---

### Post by ozanne on 2013-05-21
I have a dual boot arrangement on my laptop; ubuntu is great but I am getting messages that I am running out of space.
The message says something like, "This computer only has 845MB remaining. You can free up space by deleting unused programs."
I have a large swap space that seems unused. Do I need to increase the size of the partition where the linux system resides?
I have been disregarding this warning but am concerned I may be heading for a catastrophic failure. Any advice will be appreciated.
I am na newbie and have searched the forums but have been unable to find similar issues.
Brief synopsis of my computer:
Recovery partition; /dev/sda1 10GB
System Reserved partition; /dev/sda2 105MB
Windows partition; /dev/sda3 336GB
swap space partition; /dev/sda4 293GB
linux file system partition; /dev/loop0 19GB

---

### Post by Cheesemill on 2013-05-21
Can you post the output of the following commands please...
```
df -h
sudo parted -l
```

---

### Post by ozanne on 2013-05-21
Filesystem      Size  Used Avail Use% Mounted on/dev/loop0       18G   16G  575M  97% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  1.3M  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.0G  984K  3.0G   1% /run/shm
/dev/sda3       314G  176G  138G  57% /host

Model: ATA SAMSUNG HM641JI (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system     Flags
 1      1049kB  10.4GB  10.4GB  primary  ntfs            diag
 2      10.4GB  10.5GB  105MB   primary  ntfs            boot
 3      10.5GB  347GB   336GB   primary  ntfs
 4      347GB   640GB   293GB   primary  linux-swap(v1)

---

### Post by Impavidus on 2013-05-21
You have a wubi install of 18GB. It does not have a partition of its own, it exist as a file/virtual partition inside your windows partition. If you wish you can increase this virtual partition to 30GB: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

That swap partition is insanely large. You may want to turn that in some proper Linux partitions and move your wubi install there.

---

### Post by Uly55es on 2013-05-21
Hi ozanne, first of all I'd try to understand if the error message is talking about RAM (which would sound weird, since you can free it up *closing* unused programs, not actually *deleting* them) or if the problem is about a too small partition, as you suggest (meaning ROM). Open the terminal (ALT+CTRL+T) and type:

---

### Post by Uly55es on 2013-05-21
Sorry, I made a mess with the forms (I wrote the post half an hour ago, so it wasn't up to date anymore... :) )
It seems that your linux filesystem partition (/dev/loop0) is running out of memory (97% used, as df reports).
I'd suggest you to shrink the swap (it's pointless to keep it so huge :) ) and use some of the freed space to give /dev/loop0 more breath...
Hope it can help!

---

### Post by oldos2er on 2013-05-21
ozanne, since memory (RAM) and hard disk space are two very different things, I've changed the thread title. 

You could install Ubuntu on your current swap partition. 293GB is plenty of room (and then some) for an Ubuntu installation.

---

### Post by oldfred on 2013-05-21
Swap is just a partition used by a full install of Ubuntu as RAM overflow. Or if you startup more applications at one time then it may use swap. Swap may also be used if you hibernate and then it needs to be the same size as RAM in GiB not GB.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
    
 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Since you are not using the swap partition with a wubi install, you should just convert it to an extended partition. You can only have 4 primary partitions and right now swap is your 4th partition. But then in the extended partition you can create as many logical partitions as you need.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by ozanne on 2013-05-25
Update:
Thanks for your responses - I succeeded in executing the "wubi-move" script and relocated my install to a free partition. Now the commands above yield:
jrider@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4       222G   14G  197G   7% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  1.2M  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.0G  656K  3.0G   1% /run/shm
jrider@ubuntu:~$ sudo parted -l
[sudo] password for jrider: 
Model: ATA SAMSUNG HM641JI (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  10.4GB  10.4GB  primary  ntfs         diag
 2      10.4GB  10.5GB  105MB   primary  ntfs         boot
 3      10.5GB  347GB   336GB   primary  ntfs
 4      389GB   630GB   242GB   primary  ext4
I think this is a fix - thanks

---

