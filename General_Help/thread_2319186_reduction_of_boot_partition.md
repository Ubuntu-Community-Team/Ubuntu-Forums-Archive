---
title: "reduction of /boot partition"
date: 2016-04-01
forum: General Help
---

### Post by charitosha on 2016-04-01
Greetings everyone!
I have a netboot with one hdd of 250 Gb. That hdd is one (back then i didn't know better...) ext4 partition 
How is it possible to resize this one big partition (specifically to make it smaller) and make another one? (or other ones?). 
Since this partition has boot flag it cannot be unmounted right?(It is the only OS I've got here).
I am thinking to use something like parted resize and then mke2fs.
(i chose mke2fs because the man pages clearly states the it supports ext4).

I need guidance in what to use and how.
My kernel version: 3.2.0-82-lowlatency-pae
I have ubuntu 12.04 lts

```

haris@Mini-210:~$ sudo parted -l
[sudo] password for haris: 
Model: ATA Hitachi HTS72502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  248GB  248GB   primary   ext4            boot
 2      248GB   250GB  2133MB  extended
 5      248GB   250GB  2133MB  logical   linux-swap(v1)



```

P.S. Just noticed something. Why it says Partition Table : msdos???
 On this netbook I used to have windows 7 starter. However i deleted it and only have ubuntu.

---

### Post by frostschutz on 2016-04-01
The boot flag doesn't matter / doesn't change the process in any way...

Since you're only using 2 partitions so far, you can easily shrink the filesystem with resize2fs, then shrink the partition accordingly, and create a new primary partition in the free space.

Since the other partition is only swap, you could delete that as well, and create sda2, sda3, ... as to your liking (including the creation of a new swap partition) once you've shrunk sda1.

If you're unsure about the details, a livecd with gparted should be able to handle it as well...

---

### Post by charitosha on 2016-04-01
In the man pages of resize2fs says that It  can  be  used  to enlarge or shrink an unmounted file system, but i don't think that i can unmount my hdd since its the only one.
Or do you mean to delete the swap and then expand it? But will this work since I don't have unallocated space?

---

### Post by grahammechanical on 2016-04-01
Do not get distracted. Except that certain things are the way they for reasons going back in history. You have on the hard disk MBR or msdos partitioning. This means that there is a limit of 4 primary partitions. You have used up 2 of the 4 primary partition limit.

#1 sda1 = 248 GB formatted Ext4 and is the partition with Ubuntu in and it s a primary partition.
#2 sda2 = 2133 MB. It is a special primary partition called an extended partition.
#3 sda3 = 2133 MB. It is inside the extended partition sda2. That is why they are the same size. It is called a Logical partition and it is the swap partition.

Having an extended partition is useful because although we are limited to 4 primary partitions by having an extended partition we can have, in effect, any number of Logical partitions inside the extended partition. All that is needed is unallocated space to create them from.

We do not usually resize partitions from Ubuntu running from a hard disk. To start with, an installed Ubuntu does not have a partitioner utility installed by default. Instead we use the Ubuntu Live session. That does have a partitioner utility installed and it is called Gparted. And we can then resize the partition Ubuntu is installed in because it will not be mounted.

You have to decide if you want to use up one of the 2 remaining allocated primary partitions or create more logical partitions inside the extended partition. You can use Gparted to resize/shrink sda1 to create unallocated space and then create a primary partition out of the unallocated space. You can only do that twice.

Or after creating unallocated space resize/expand sda2 (extended partition) into the unallocated space and in effect move it into the extended partition and then create a logical partition out of the unallocated space. You can do this more than twice.

Before you can resize the extended partition you will have to use Gparted to turn the swap partition off. It is called swap off. The live session mounts the swap partition in case it needs to use it. So, swap will be on and needs to be off to resize the extended partition.

Here is the HowTo with illustrations

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by charitosha on 2016-04-01
So basically the only way to do it is with live usb because then i can unmount the sda1?
That is a solution, but i was wondering if it's possible to do it at run time. For example to say which blocks you want to free...

---

### Post by ian-weisser on 2016-04-01
> **charitosha said:**
> So basically the only way to do it is with live usb because then i can unmount the sda1?
That is a solution, but i was wondering if it's possible to do it at run time. For example to say which blocks you want to free...

You can change any partition you wish anytime you wish...as long as the target partition is unmounted.
If you store your filesystem and your partition-editing applications on that target partition, then you have a chicken-and-egg problem.
It's possible to cleverly overcome that problem several ways...but is generally not worth the effort and complexity.

---

### Post by charitosha on 2016-04-02
Well I made a gparted live usb, and everything was straight forward. The hdd (/dev/sda) was unmounted and I could modify it as usual.
Now i have an extra partition!
One quick question before I mark it as solved...  #-o
/dev/sda is of 232.89 Gb of capacity, however the hdd is of 250 Gb. Where are those 17.11 Gb that are missing?

---

### Post by oldfred on 2016-04-02
MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space for superuser.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)
More confusion?
[http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release](http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release)
1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes
Chart with more conversions -  JKyleOKC
[http://ubuntuforums.org/showthread.php?t=2240118&p=13101706#post13101706](http://ubuntuforums.org/showthread.php?t=2240118&p=13101706#post13101706)
160 GB (gigabytes) = 149.01 GiB (gibibytes)
sudo parted -s /dev/sda unit GB print
sudo parted -s /dev/sda unit GiB print

---

### Post by charitosha on 2016-04-02
250 GB is more and less 233 GiB. Damn, thought all the time that GB and GiB is the same...

---

