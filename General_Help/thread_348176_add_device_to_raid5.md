---
title: "add device to raid5"
date: 2007-01-28
forum: General Help
---

### Post by vdhagen on 2007-01-28
Hi,
when I created a raid5 array, one of the disks broke down. I created the array with one disk less, replaced the defective drive and want to add it now to the array.

Using mdadm 2.4.1, Linux Ubuntu 2.6.17 I try to add /dev/hdd1 to /dev/md0. Apparently I have to "add" the device first before the array can "grow" (couldn't find this in the manual, though).

Unfortunately:
mdadm -G /dev/md0 -n4 --backup-file=...
leads to:
mdadm: Need to backup 384K of critical section..
mdadm: Cannot set device size/shape for /dev/md0: Invalid argument

Any comment if this should be possible or if I made a mistake?

Is the quickest way to create the new array from scratch?

The old(?) linux-raid faqs I found (2002-2004) usually say "diificult" or even "impossible" about adding devices to raid 5.

Apparently I can't specify the device(s) that should become active. If I have an array with 3 active disks and two spares what would happen when I order "grow -n4" (assuming it would work). Would the system just pick the "next" disk?

There are other strange things: The manual of mdadm lists "-x" as option for "create, build or grow". At run time, though, mdadm states "option -x not valid in grow mode".

Helpful comments will be appreciated.
Oskar

P.S.
mdadm -D /dev(md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Dec 27 19:13:32 2006
     Raid Level : raid5
     Array Size : 488391808 (465.77 GiB 500.11 GB)
    Device Size : 244195904 (232.88 GiB 250.06 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jan 28 17:48:05 2007
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f2211e32:3cefb926:62d2bc1f:91ce82a6
         Events : 0.136505

    Number   Major   Minor   RaidDevice State
       0       3        1        0      active sync   /dev/hda1
       1       3       65        1      active sync   /dev/hdb1
       2      22        1        2      active sync   /dev/hdc1

       3      22       65        -      spare   /dev/hdd1


P.P.S. It is not a very "general" question but there are many raid-posting in this group.

---

### Post by kosmic on 2007-01-28
You are doing everything rigth, but the problem is that the Ubuntu kernel 2.6.17 doens't support very well RAID 5.

To make this problem go away update your Ubuntu kernel to at least 2.6.19

You can read this -> [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) if you want to upgrade your kernel

After that it should be so simple as :

[B]# mdadm &#8211;add  /dev/md0 /dev/sd*
[/B]**# mdadm &#8211;grow /dev/md0 &#8211;raid-disks=4 (this is the Total number of disk you have)**
[B] 
[B]Hope it helps you out

[/B][/B]Also a small sugestion if you have a lot of disks (At least 4) I prefer to make a RAID 1 + 0, it is faster and more reliable

---

### Post by vdhagen on 2007-01-29
I am not there yet. :-(  But thanks for the tip. :-)

I compiled the kernel 2.6.19.2 and got it running. However, there are all kinds of funny messages concerning my array, e.g.

[LIST=1]
mdadm -A /dev/md0
mdadm: ARRAY line /dev/md0 has no identity information.
mdadm: Unknown keyword UUID=f2211e32:3cefb926:62d2bc1f:91ce82a6
mdadm: /dev/md0 not identified in config file.
[*]mdadm --grow /dev/md0 --raid-disks=4 --backup-file=/home/vdhagen/md0-backup
mdadm: Need to backup 384K of critical section..
mdadm: Cannot set device size/shape for /dev/md0: Device or resource busy
[*]mount /dev/md0 /mnt/nas
mount: you must specify the filesystem type
[*]mdadm --assemble --scan
mdadm: ARRAY line /dev/md0 has no identity information.
mdadm: Unknown keyword UUID=f2211e32:3cefb926:62d2bc1f:91ce82a6
mdadm: No arrays found in config file
[/LIST]

I am somewhat lost. With the old kernel 2.6.17.10 there is no problem in using the array.

Oskar

P.S. The system serves mainly as NAS and for a backup device 25% overhead as in raid5 should suffice. In raid 1 + 0 it would be 50%, right?

---

### Post by dcstar on 2007-01-29
> **vdhagen said:**
> 
.......
P.S. The system serves mainly as NAS and for a backup device 25% overhead as in raid5 should suffice. In raid 1 + 0 it would be 50%, right?

In any RAID-5 array (of equal sized drives) one drive is essentially lost to "overhead".

If you have 3 drives, then the total space available is the sum of two of the drives, if you have 4 then it is the sum of 3 etc. etc.

Keep in mind that the more drives in any array, the more (statistically) likely a failure will be - an array of 4 drives is twice a likely to have a drive failure than an array of 2 for any MTBF.

That is the trade-off in RAID-5, the more drives you have in an array the less space your lose to "overhead", but you increase the chance of a failed drive (sooner or later) with each one you add.

---

