---
title: "How to make filesystem recognize growth of a RAID array?"
date: 2008-03-03
forum: General Help
---

### Post by OfficeLinebacker on 2008-03-03
Hi.  

Running 7.10 Gutsy desktop on a socket 939, Athlon 64 X2 platform.

I set up a nice RAID-5 array using 4x320GB disks.  That gave me a 895GB device.  I then purchased 4 500GB disks and swapped them out, 1 x 1, until the same array existed, only on 500GB disks.  I then used mdadm to grow the array and it worked, giving me a 1.4TB array.  However, the filesystem still thinks it's 895GB.  In the mdadm man page, it says


[FONT=Arial Black]   SIZE CHANGES
       Normally  when  an  array  is built the "size" it taken from the smallest of the drives.  If all the small drives in an arrays are, one at a time,
       removed and replaced with larger drives, then you could have an array of large drives with only a small amount used.  In this situation,  changing
       the  "size"  with "GROW" mode will allow the extra space to start being used.  If the size is increased in this way, a "resync" process will start
       to make sure the new parts of the array are synchronised.

       Note that when an array changes size, any filesystem that may be stored in the array will not automatically grow to use the space.  The filesystem
       will need to be explicitly told to use the extra space.
[/FONT]  
So how do I explicitly tell the filesystem to use the extra space?

In case it helps, output from some commands;

```
jonathan@HOMESTAR:~$ df -hlP
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1              35G  2.9G   30G   9% /
varrun                2.0G  748K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   92K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
/dev/md0              895G  515G  335G  61% /var

``````
jonathan@HOMESTAR:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Sep 12 10:49:52 2007
     Raid Level : raid5
     Array Size : 1465159488 (1397.29 GiB 1500.32 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Mar  3 11:41:24 2008
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : e0fd9992:82d2c367:bda83a06:4bf9f3e6
         Events : 0.112675

    Number   Major   Minor   RaidDevice State
       0       8       48        0      active sync   /dev/sdd
       1       8        0        1      active sync   /dev/sda
       2       8       32        2      active sync   /dev/sdc
       3       8       16        3      active sync   /dev/sdb

```

---

### Post by fjgaude on 2008-03-03
I've never done what you are doing. I find this in the man pages: 
```

-z, --size=
              Amount (in Kilobytes)  of  space  to  use  from  each  drive  in
              RAID1/4/5/6.   This  must  be  a multiple of the chunk size, and
              must leave about 128Kb of space at the end of the drive for  the
              RAID  superblock.   If  this is not specified (as it normally is
              not) the smallest drive (or partition) sets the size, though  if
              there is a variance among the drives of greater than 1%, a warn&#8208;
              ing is issued.

              This value can be set with --grow for RAID level 1/4/5/6. If the
              array  was created with a size smaller than the currently active
              drives, the extra space can be accessed using --grow.  The  size
              can  be given as max which means to choose the largest size that
              fits on all current drives.
```

Use the --grow command with --size=500000, as I see it. But the size entered should be divisible by 64, like 486400, maybe close to 488386496 from the -D mdadm read you showed us.

Good luck, but do let us know how you are doing.

---

### Post by OfficeLinebacker on 2008-03-03
> **fjgaude said:**
> I've never done what you are doing. I find this in the man pages: 
```

-z, --size=
              Amount (in Kilobytes)  of  space  to  use  from  each  drive  in
              RAID1/4/5/6.   This  must  be  a multiple of the chunk size, and
              must leave about 128Kb of space at the end of the drive for  the
              RAID  superblock.   If  this is not specified (as it normally is
              not) the smallest drive (or partition) sets the size, though  if
              there is a variance among the drives of greater than 1%, a warn&#8208;
              ing is issued.

              This value can be set with --grow for RAID level 1/4/5/6. If the
              array  was created with a size smaller than the currently active
              drives, the extra space can be accessed using --grow.  The  size
              can  be given as max which means to choose the largest size that
              fits on all current drives.
```Use the --grow command with --size=500000, as I see it. But the size entered should be divisible by 64, like 486400, maybe close to 488386496 from the -D mdadm read you showed us.

Good luck, but do let us know how you are doing.

That's from the mdadm man page--that's where the quote in my original post is from.

I did that part already.  From the mdadm side, its' fine--it knows the disks are 500GB each and lists the usable size as 1.5TB.

It's the OS/ext3/filesystem side I need to work with to tell it that it's now a 1.5TB filesystem, not a 900GB.

Make sense?

---

### Post by fjgaude on 2008-03-03
Did you observe the array resyncing to the new size? Using something like:

```
sudo watch cat /proc/mdstat
```

You mean that when you access the array in Ubuntu the disk size shows something less than 1.5T, like 900G?

When we first create an array, we then use mkfs to create the file system. I'm at a loss why you are getting what you do. Seems like the --size command would have changed the array size.

Say, what version of Ubuntu are you using?

Maybe someone else here has an answer.

Keep us informed, please.

---

### Post by OfficeLinebacker on 2008-03-03
> **fjgaude said:**
> Did you observe the array resyncing to the new size? Using something like:

```
sudo watch cat /proc/mdstat
```You mean that when you access the array in Ubuntu the disk size shows something less than 1.5T, like 900G?

When we first create an array, we then use mkfs to create the file system. I'm at a loss why you are getting what you do. Seems like the --size command would have changed the array size.

Say, what version of Ubuntu are you using?

Maybe someone else here has an answer.

Keep us informed, please.

Updated the first post with version info, 7.10 desktop.  Using 4 SATA ports on mobo to do it, booting off an IDE drive.  

I did not watch the resync, but the LEDs indicating activity did their thing, and then checked with the mdadm command above and see the output that you see in the first post.

I'll quote you again here because you've distilled my problem to the essence:

> **fjgaude said:**
> You mean that when you access the array in Ubuntu the disk size shows something less than 1.5T, like 900G?

Exactly.

Maybe I need to use mkfs?  I perused the man page but I didn't read it w4w.  But I don't want to lose the data I already have on there.

To summarize:

problem with /dev/md0

mdadm says 1.5TB device

df says 900GB device

I want the full 1.5TB of capacity.

Thanks,
Jonathan

---

### Post by fjgaude on 2008-03-03
I don't think I have any suggestions... If you mkfs now I think you will lose all your data.

Let us know what happens, if you solve the issue.

---

### Post by lswest on 2008-03-03
Well, i know when you use a partitioner, such as GParted, if you resize your ext3 partition, it expands the filesystem to the size of the partition, maybe you can do something similar with the RAID array?  I'm not honestly sure, never used RAID.

---

### Post by Oldsoldier2003 on 2008-03-03
I don't have an answer, but maybe you could ask a mod to move this to the server forum or ask there as well? The folks that haunt that forum might be more helpful. Just a thought...

---

### Post by koenn on 2008-03-03
I remember a similar problem being posted a while back - with a very good explanation of why this can be problematic / hard to do, plus a recipy to work around that. 

maybe try searching the forums ?

---

### Post by OfficeLinebacker on 2008-03-03
Thanks so much for your helpful observations/suggestions.  I'll ask a mod to move it.  In the meanwhile,

Using Gparted or a partition editor--GREAT idea.  I'll try that right away.

Makes sense that mkfs would obliterate data.


> **koenn said:**
> I remember a similar problem being posted a while back - with a very good explanation of why this can be problematic / hard to do, plus a recipy to work around that. 

maybe try searching the forums ?

---

### Post by lswest on 2008-03-03
haha i don't know about my idea being great, but i hope it works :P

---

### Post by fjgaude on 2008-03-03
Gparted does know raid arrays... only shows them and their size.

---

