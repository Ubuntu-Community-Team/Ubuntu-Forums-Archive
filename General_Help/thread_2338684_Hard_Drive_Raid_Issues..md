---
title: "Hard Drive Raid Issues."
date: 2016-09-30
forum: General Help
---

### Post by cooljacob204 on 2016-09-30
So I kinda have a weird issue. Not totally sure if this is the right place to ask but its general help :P

A while back I was running two of my 1tb HDDs in raid 0 using my motherboard software. I broke that raid a few years ago. I never had issues mounting or displaying my drives on Windows.

Recently I installed Ubuntu and my HDD will not mount and seem to be stuck in some sort of bad raid configuration. My guess windows somehow messed up the drives.

Two blank drives show up which look like this:

[IMG]https://puu.sh/rtadE/79d4470d9a.png[/IMG]

and this:

[IMG]https://puu.sh/rtahy/f5eb673265.png[/IMG]

Running cat /proc/partitions shows:

major minor  #blocks  name


   1        0      65536 ram0
   1        1      65536 ram1
   1        2      65536 ram2
   1        3      65536 ram3
   1        4      65536 ram4
   1        5      65536 ram5
   1        6      65536 ram6
   1        7      65536 ram7
   1        8      65536 ram8
   1        9      65536 ram9
   1       10      65536 ram10
   1       11      65536 ram11
   1       12      65536 ram12
   1       13      65536 ram13
   1       14      65536 ram14
   1       15      65536 ram15
   8        0  250059096 sda
   8        1  249133056 sda1
   8        2     460800 sda2
   8        3     460800 sda3
   8       16  976762584 sdb
   8       32  976762584 sdc
   8       33  976760832 sdc1
   8       48  976762584 sdd
   8       64  244198584 sde
   8       65  227506176 sde1
   8       66          1 sde2
   8       69   16690176 sde5
   8       80  976762584 sdf
   8       81  976760832 sdf1
 252        1 1953124992 dm-1
 252        2  908105142 dm-2
 252        3  976826554 dm-3
 252        4        223 dm-4

This has been my main issue with switching to Linux, however I got a new SSD for it and class projects are starting to require Unix. Also Windows 10 Anniversary update broke its ability to read the hard drives so I miss out on a lot of important updates. 

Any help with solving this issue would be greatly appreciated, I don't have anything to back up both drives to and wipe it, they are both almost full. Full of steam games and other media. I just wish to read the drives until I can buy a back up drive to fix this issue.

Sorry if I missed some information to provide. It's been a while since I had to ask on forums myself since most of my problems have already been asked :P

---

### Post by TheFu on 2016-09-30
Sorry if this seems harsh. Someone should have explained this to you sooner.

Without the ability to use a backup, I got nuthin to help.  RAID0 - seriously?  You like to live dangerously - like driving down the wrong side of a busy road.  RAID0 is for video editors who need tons of temporary work space during the day, but put their projects on other storage overnight AND have perfect backups.

BTW, using MB RAID is asking for trouble.  All the slow performance of SW-RAID, but all the inflexibility of HW-RAID. I'm sure there are reasons to use it, but cannot think of any.  SW and HW RAID have good reasons to be used - both do.

When RAID is used on Linux the devices are marked as "RAID." It is protection. Look for how to remove those RAID tags. All data may be lost, I dunno. After that, you might be able to recover the data. Might.  [http://www.tomshardware.com/forum/171556-32-previously-raid-format-help](http://www.tomshardware.com/forum/171556-32-previously-raid-format-help) - seems wiping the data is going to be the result.

Get thee some backups, dude.  RAID **never** replaces backups, even RAIDz2 or RAID10.  There are 2 purposes for RAID and 1,000+ purposes for backups.

**sudo parted -l** would be helpful. Use code tags when posting, not images. Please be kind to people with low bandwidth.

Of course, I could be misreading everything completely wrong.

---

### Post by oldfred on 2016-09-30
If you broke the RAID before, you may have left RAID meta-data on drive, so drive still looks like RAID to Linux.

This used to be the commands to remove the motherboard RAID. But see note below.
       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings 

But this has happened since, and I do not now know a new command, old one may still work. I do not use RAID. But be sure to have good backups.
      
 dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids

---

### Post by cooljacob204 on 2016-10-05
Been a few days since I have had the time to test this. oldfreds method worked, can now see all the drives. Thanks for the help guys.

---

