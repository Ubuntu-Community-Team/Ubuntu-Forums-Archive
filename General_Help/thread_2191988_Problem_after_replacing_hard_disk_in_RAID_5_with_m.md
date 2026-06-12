---
title: "Problem after replacing hard disk in RAID 5 with mdadm"
date: 2013-12-05
forum: General Help
---

### Post by msteinbichler on 2013-12-05
Hi,

First of all, I am new to this forum and would like to say hello to everyone!

Currently I am facing some problems after replacing a faulty hard disk in my RAID 5 array.
Some general information first:
 - Ubuntu version 12.04.3 LTS
 - One separate hard disk (SSD) is running the OS (/dev/sda1)
 - A RAID 5 Array is using /dev/sdb1 /dev/sdc1 /dev/sdd1 and /dev/sde1

After hard disk /dev/sdd1 failed I shutdown the server, took it out and put a new one (almost the same disk) on the same slot
At this point the array was working like this:
```
Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed
       3       8       65        3      active sync   /dev/sde1
```

Using fdisk I copied the Partition table of /dev/sdc to /dev/sdd
then I added the disk with 
```
sudo mdadm /dev/md0 --add /dev/sdd1
```

It started rebuilding fine. After some time the array was in following state:
```
Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed
       3       8       65        3      active sync   /dev/sde1
       4       8       49        -      spare   /dev/sdd1
       5       8       17        -      faulty spare   /dev/sdb1
```

When this hapens I stopped the array and tried to reasemble it with the 3 initially working disks. Then I get following error
```
martin@Martin-Server:~$ sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sde1
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
```

Only if I start the re-assembly with --force I can re-assemble the array
```
martin@Martin-Server:~$ sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sde1 --force
mdadm: forcing event count in /dev/sdb1(0) from 120146 upto 120153
mdadm: /dev/md0 has been started with 3 drives (out of 4).
```

However if I then try to add the new disk again - I have the same problem.

I would really appreciate some good ideas how to get my RAID 5 to work with 4 disks again :)

Many Thanks in advance,
Martin

---

### Post by SaturnusDJ on 2013-12-07
Look at S.M.A.R.T. for all devices. Maybe something is wrong with a current member.
```
smartctl -a /dev/sda
```
etc.

---

### Post by msteinbichler on 2013-12-08
I executed it for all hard disks - I don't see anything unusual...
Attached you can find the output in two text files. Btw, sdd is the new disk

---

### Post by SaturnusDJ on 2013-12-08
/dev/sdb isn't in very fine shape.
Lots of Current Pending Sectors. They should become Reallocated Sectors.

Any clue in the syslog maybe?

---

### Post by msteinbichler on 2013-12-08
I attached the syslog.
Unfortunately I don't understand much of it - but it seems you are right that there is something wrong with sdb.
Probably I'll need to replace this disk as well?

If yes, do you see any way to recover the RAID without having to copy all data to an external drive and back again?

Btw, it is still the case, that the array works fine, if I just re-assemble sdb, sdc and sde with --force
Thank you very much for your help!

---

### Post by SaturnusDJ on 2013-12-08
/dev/sdb seem to be broken indeed.

Unless anyone else has a better idea I suggest to rescue this disk to a new one and try from there. Rescuing a disk is a special process that's not the same as a regular dd if/of. [http://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue](http://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue)

---

### Post by msteinbichler on 2013-12-08
At least the two disks didn't fail exactly at the same time. Since I already have a full external backup, I am pretty relaxed anyhow :)
Thank you for your suggestion. I am currently on a business trip, but I will follow it next weekend and let you know about the result

---

### Post by msteinbichler on 2013-12-21
First of all: Thanks again for helping me! 
The good news: My RAID is now finally working with four disks - and I didn't loos any data! I did it like you suggested. I bought another new hard disk, cloned the faulty /dev/sdb and started the array.

The only problem: The new hard disk has physical sector size of 4096 but the partition table was cloned as follows:
```
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4eb6a609


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   83  Linux
Partition 1 does not start on physical sector boundary.

```

What are the implications of this? Should I do something about it, or can I just leave it like it is.

By the way - while working on it I found out, that I also created (long time ago) a different partition table when I added the fourth disk. Before this, the RAID was working with 3 disks only.
Now I have following situation for this disk:
```
Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

This happens, if you work with this stuff only once in 2 years :)

Thanks and Regards,
Martin

---

### Post by SaturnusDJ on 2013-12-31
```
parted /dev/sdb align-check m 1
```

m = minimal, it checks for 4k alignment
o = optimal, it checks for 1M alignment

1 = partition number on device.

If there is no alignment, performance may suffer.

---

### Post by msteinbichler on 2014-01-01
It says
```
1 not aligned
```

> **SaturnusDJ said:**
> If there is no alignment, performance may suffer.

What kind of performance issues are we talking about here? Generally I am accessing the array only via 1 Gbps ethernet - therefore I supose the bottleneck will anyway be the network. Correct?

---

### Post by SaturnusDJ on 2014-01-01
If your array is tuned well, ethernet indeed will be the bottleneck.

I don't know the performance drop...there is some information about this on the web.

Use this to quickly test your array speed:
```

dd if=/dev/zero of=/mount/raid/testfile bs=1M count=2000
echo 3 > /proc/sys/vm/drop_caches
sync
dd if=/mount/raid/testfile of=/dev/null bs=1M
echo 3 > /proc/sys/vm/drop_caches
sync
hdparm -t /dev/md0
rm -rfv /mount/raid/testfile

```

---

### Post by msteinbichler on 2014-01-01
I executed the steps. However I wasn't able to write to /proc/sys/vm/drop_caches

It seems to me the read performance is very good, but writing is a little poor. What would you say? Honestly I don't really know what speed I can expect...

```

martin@Martin-Server:~$ dd if=/dev/zero of=/mnt/data/testfile bs=1M count=2000
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 59.1842 s, 35.4 MB/s
martin@Martin-Server:~$ sudo echo 3 > /proc/sys/vm/drop_caches
-bash: /proc/sys/vm/drop_caches: Permission denied
martin@Martin-Server:~$ sync
martin@Martin-Server:~$ dd if=/mnt/data/testfile of=/dev/null bs=1M
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 10.5092 s, 200 MB/s
martin@Martin-Server:~$ sync
martin@Martin-Server:~$ sudo hdparm -t /dev/md0
/dev/md0:
 Timing buffered disk reads: 598 MB in  3.27 seconds = 183.15 MB/sec

```

---

### Post by SaturnusDJ on 2014-01-01
Aah my bad. Put the commands in a bash script and run it as root.
Maybe the failure of drop cache explains your higher read. At this moment the difference between read and write is too much. Current write speed is way below 1GB/s ethernet.

---

### Post by msteinbichler on 2014-01-02
I put it in a bash script and executed it two times. Speed was a little better than yesterday, but this could be because I was downloading something when I tried it yesterday:

```

martin@Martin-Server:~$ sudo ./testSpeed2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 47.62 s, 44.0 MB/s
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 9.47341 s, 221 MB/s


/dev/md0:
 Timing buffered disk reads: 924 MB in  3.01 seconds = 307.35 MB/sec
removed `/mnt/data/testfile'
martin@Martin-Server:~$ sudo ./testSpeed
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 48.701 s, 43.1 MB/s
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 9.17216 s, 229 MB/s


/dev/md0:
 Timing buffered disk reads: 938 MB in  3.01 seconds = 312.10 MB/sec
removed `/mnt/data/testfile'

```

---

### Post by SaturnusDJ on 2014-01-03
Is S.M.A.R.T. okay for these disks? You replaced the bad ones?

Do you have non raid partitions or space on the disks for individual testing?

---

