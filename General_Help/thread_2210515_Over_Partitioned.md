---
title: "Over Partitioned ?"
date: 2014-03-10
forum: General Help
---

### Post by newbie2244 on 2014-03-10
I'm not sure whether this is the place to ask/post this comment/question.   SEE BELOW.  This isn't really a reply but a comment on Topsiho' comment about Windows running on sda. On my system I do not have an sda partition -- only sdb1--8 and sg1--2.  My question:  [nl]---Is my drive overpartitioned?  I ran[/nl]```
 sudo parted -l
``` and this is the output:

```
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  420MB  419MB   ntfs         Basic data partition          hidden, diag
 2      420MB   693MB  273MB   fat32        EFI system partition          boot
 3      693MB   827MB  134MB                Microsoft reserved partition  msftres
 4      827MB   370GB  370GB   ntfs         Basic data partition
 5      370GB   496GB  126GB   ntfs         Basic data partition
 7      496GB   720GB  224GB   ext4
 8      720GB   723GB  3430MB
 6      723GB   750GB  26.8GB  ntfs         Basic data partition          hidden
```



Originally I created a partition on my Windows8 system to install Ubuntu on it,  but, was unable to do so. I then resized it. Through a convoluted process, I did  eventually get a dual boot system. But now I have unallocated disk space, which is a waste. I also do not have swap partition for Linux. I don't know if I need one and I would like to be able to utilize the unallocated space for extended doc storage or as java programming environment. I;m not sure if this is possible. Any comments and suggestions would be helpful.

---

### Post by howefield on 2014-03-11
Post moved to own thread, almost always better than hijacking someone elses.

---

### Post by Impavidus on 2014-03-11
sda or sdb aren't partitions but drives. sda1, sda2, sdb1 etc. are partitions. I don't know why your drive is called sdb.

Partition sdb8 has about the right size for being a swap partition, but there is no partition type indicated. If you have plenty of memory you don't really need a swap partition (unless you want to hibernate), but having some is usually recommended. It only takes a tiny fraction of your hard drive. Maybe you have to format it as swap and add it to your sftab.

The partitioning scheme seems about right. There are no big chuncks of unallocated space on your drive, but some of the partitions may be invisible from Windows.

---

### Post by oldfred on 2014-03-11
With gpt you can only have 128 partitions as default but can actually change partition table to have more.
I do not think you have 128 yet, so you still are ok. :)

Windows does require some extra partitions with UEFI boot.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[URL="http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx"]http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx
[/URL]
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

[URL="http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx"]
[/URL]

---

