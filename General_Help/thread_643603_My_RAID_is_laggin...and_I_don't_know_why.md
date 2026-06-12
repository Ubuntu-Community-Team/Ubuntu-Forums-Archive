---
title: "My RAID is laggin...and I don't know why"
date: 2007-12-18
forum: General Help
---

### Post by Cr0n_J0b on 2007-12-18
I have a 5 disk RAID volume setup on my Gutsy server.  They are all SATAII and all setup under software RAID 5.  the filesystem is ReiserFS.  The issue I'm seeing is that when I click on a directory from my XP system (samba) it just lags.  Takes a couple seconds to open up.  I've also noticed that moving files within the same FS causes a good 30 second lag time.  So for example moving a set of files up one directory level...which should be fast, since I'm only updating the inodes...it takes a while to kick in.

Anyone have some thoughts?  Should I have picked a differnt fs?

The volume has about 1.5TB of files. avg file size is about 1MB.

thanks

---

### Post by fjgaude on 2007-12-18
Have you tried checking the array with mdadm?

```
sudo mdadm -D /dev/mdnn
```

That will show if any drives are failed.

---

### Post by Cr0n_J0b on 2007-12-18
I haven't looked at the mdadm -Q since I built the arrays, but I will do that later today.  I'm pretty sure that the arrays are fine...All the lights are blinking and it's brand new...but I will check.  

It seems to me that it has something to do with the filesystem.  When I go to access a directory...the drives spin like mad as, I guess, they try to build a stat of the directory listing.  Then they sit idle till I do something.  What's odd is how long it takes to do that stat.  I have lots of files, so that might be part of it, but I'm worried that it's just a function of the ReiserFS.  I've heard it's fast, but I'm not sure it was the right choice for a massive number of files.

---

### Post by fjgaude on 2007-12-18
Okay, let us see what a

```
sudo mdadm -D /dev/mdnn
```

looks like. The /dev/mdnn is the name for your array.

---

### Post by Cr0n_J0b on 2007-12-19
mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Nov 27 20:15:16 2007
     Raid Level : raid5
     Array Size : 1953503488 (1863.01 GiB 2000.39 GB)
  Used Dev Size : 488375872 (465.75 GiB 500.10 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Dec 19 07:40:12 2007
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 87e906ee:471bee8c:4c0d2395:9c0bfdf6 (local to host uNAS)
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1

here are some benches


[SIZE="5"]hdparm -t /dev/md0[/SIZE]
/dev/md0:
 Timing buffered disk reads:  440 MB in  3.01 seconds = 146.42 MB/sec

[SIZE="5"]./seeker[/SIZE] /dev/md0
Seeker v2.0, 2007-01-15, [http://www.linuxinsight.com/how_fast_is_your_disk.html](http://www.linuxinsight.com/how_fast_is_your_disk.html)
Benchmarking /dev/md0 [1907718MB], wait 30 seconds..............................
Results: 79 seeks/second, 12.56 ms random access time

[SIZE="5"]Bonnie++  [/SIZE]

Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
uNAS             4G 19202  60 24433  20 19861  13 43262  97 140359  51 515.3   2
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 24500  96 +++++ +++ 19650  97 23221  94 +++++ +++ 18930  99
uNAS,4G,19202,60,24433,20,19861,13,43262,97,

Not sure if this helps...but it's what I know.

---

### Post by fjgaude on 2007-12-20
Okay, this output shows you have a correctly working raid5 array, with good speed, but not that good.

What controller is being used to drive the SATA disks?

And sounds like you have other issues with the VMware install and perhaps with SAMBA.

I access my raid5 through SAMBA and it is fast.

We'll just have to keep looking to find the bottleneck[s].

---

### Post by Cr0n_J0b on 2007-12-20
I'm not actually using VMware at this point.  I plan to in the future, but not now.  The interface is really from mdadm to Reiserfs to Samba to my XP client and explorer.  It feels like samba is just taking time to get back the directory listing from the drives when I go to access them.  Like when you have too many files in a directory, it takes forever to list them all.  I thinking that maybe I should have picked ext3 or JFS instead of Reiser.

---

### Post by fjgaude on 2007-12-22
What's your CPU doing during this time?

Give us more details of your total system, please. Total number of files, LAN, WAN, router, things like that.

---

### Post by euk on 2007-12-23
Have (possibly) the same problem on both debian and kubuntu (mostly use debian, but checked on kubuntu also). System sometimes begin to use disks aggressively for 5-20 seconds, producing a lag (effectively lagging all other work connected to disk IO). CPU is idle. 

Software RAID6 (6 drives), ReiserFS, Q6600, 2.6.22 SMP.

My observations - system sometimes lags when:
* Opening a large directory with more than 1Tb of content (about 200 files). Sometimes it lags, sometimes not. With no depend to how the directory is opened, either via mc or through samba. Obviously this should be stat, however how can stat completely freeze all other disk IO?
* During operations with large files, such as copying and/or deletion.

I'm assuming the problem is in ReiserFS, I can hardly imagine what could cause a simple software RAID to produce such behavior. I think that possible reasons are:
* Some strange implementation of stat on reiserfs blocking all other simultaneous IO. Maybe conflicts/deadlocks on a SMP kernel?
* Something on a system level of FS, such as defragmentation. I've heard that ReiserFS family autodefragments, anyone knows details?
* Something weird with journal management. Is there a kind of journal truncation on Reiser, or it reuses the data written to the journal when performing massive writes?

ReiserFS seems rather good at all points, except these lags and lack of managing utilities. Moving to other FS is currently not an option... At these point I consider myself not mature enough to diagnose the problem. I'm giving up. Can anyone advise?

---

