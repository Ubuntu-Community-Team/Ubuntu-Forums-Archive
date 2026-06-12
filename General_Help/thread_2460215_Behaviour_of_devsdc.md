---
title: "Behaviour of /dev/sdc"
date: 2021-04-05
forum: General Help
---

### Post by ulrichmuc2 on 2021-04-05
/dev/sdc is a microSD card. I can access /dev/sdc1 but not /dev/sdc.
gparted /dev/sdc gives me " Could not stat device sdc - no such file or directory."
gparted /dev/sdc1 works as expected.
Is this normal behaviour?

---

### Post by yancek on 2021-04-05
Yes that is normal behavior.  sdc refers to the physical device while sdc1 refers to a partition on that device on which a filesystem exists.

>  gparted /dev/sdc gives me " Could not stat device sdc - no such file or directory." 

That means there is no mount point for sdc which is standard and expected and not a problem.  It is possible to create a filesystem and mount point for a device (sdc) but that is not the way it is generally done.

---

### Post by ulrichmuc2 on 2021-04-05
However, another SD card which contains an ubuntu image can be seen by gparted as /dev/sdc.
What is the difference?

---

### Post by The Cog on 2021-04-05
It is possible to place a filesystem directly on a disk (or USB). I think this would be known as a raw disk. This would show up as (e.g.) /dev/sdc.
Alternatively, you can place a partition table on the disk, and put a filesystem in each partition. In this case /dev/sdc is not itself mountable because it doesn't contain a filesystem, it contains a partition table. But the filesystems in the partitions 1, 2, 3... would show up as /dev/sdc1, /dev/sdc2, /dev/sdc3 etc.
Using multiple partitions allows for installing multiple operating systems, and other applications where you want to act as though you have several separate disks.
This may help by giving you a slightly graphical listing or the partitions:
```
lsblk -f
```

---

### Post by ulrichmuc2 on 2021-04-06
Thanks a lot. I am now convinced that one of my SD-cards is unreadable. Any way to fix this?

---

### Post by yancek on 2021-04-06
> I am now convinced that one of my SD-cards is unreadable. Any way to fix this?         

Why?  What device and what led you to that conclusion?  You will need to provide more specific information if you want help.

If you have written an Ubuntu image (iso file) to a device it will show under the device (sdc).

---

### Post by TheFu on 2021-04-06
> **ulrichmuc2 said:**
> Thanks a lot. I am now convinced that one of my SD-cards is unreadable. Any way to fix this?
SD cards fail.  They hit their write count limit and stop working.  If that has happened, there isn't anything that can be done to fix it.
But, for the cost of 1 more write, you can 
[LIST=1]
[*]zero out the entire SD card, 
[*]put a partition table onto it, then 
[*]create at least 1 partition and 
[*]format it to hold data.
[/LIST]
Most of that can be accomplished using gparted. Run it with **sudo -H gparted**.

If we just want to put an ISO onto it, no need to zero or partition or format anything, since the ISO will contain all of that formating/partitioning already.
```
sudo cp /path/to/some-file.iso  /dev/sdZ
```

That will slam the some-file.iso onto sdZ. Be 100% certain that sdZ is the correct device for the whole drive, not for a partition and definitely NOT for some other drive.  It would be really bad if the wrong storage device was the target - that would be a bad day. Total data loss on it.

We can use dd, ddrescue and a number of other tools to accomplish the same thing.  Recently, I've become convinced that using cp is by far the easiest way and most people understand the cp command already.

Here's a resulting SD that had an ISO written to it:
```
Filesystem                                       Type     Size  Used Avail Use% Mounted on
/dev/sdc1                                        iso9660   17M   17M     0 100% /mnt/1
```
There's no way to see/access sdc ... only the partition.
```
$ ls -la /mnt/1/
total 16542
drwxr-xr-x 1 root root    2048 Aug  8  2018 ./
drwxr-xr-x 7 root root    4096 Sep  4  2020 ../
-rw-r--r-- 1 root root 8301472 Aug  8  2018 bzImage
-rw-r--r-- 1 root root 8629044 Aug  8  2018 initrd
drwxr-xr-x 1 root root    2048 Aug  8  2018 isolinux/
```
The ISO file in my example above is a bootable driver update ISO for Samsung SSDs. As you can see, it is 17M, very tiny.

---

### Post by ulrichmuc2 on 2021-04-06
The sd-card is put into an usb-cardreader.
gparted /dev/sdc gives me: Error opening /dev/scd: No medium found

With two other SD-cards, however, gparted shows iso9660 on /dev/sdc or fat32 on /dev/scd1 respectively.
That makes me believe that the other card is broken.

When I try to dd an image onto the card, dd claims to have read/written 4010784 records, but gparted still cannot read it.

---

