---
title: "Software RAID5 issues on reboot."
date: 2007-09-21
forum: General Help
---

### Post by tekati on 2007-09-21
After a reboot I noticed that my RAID5 did not come up.  This is /dev/md3

mdadm -D /dev/md3
mdadm: md device /dev/md3 does not appear to be active.

mdadm -E /dev/md3
mdadm: No md superblock detected on /dev/md3.

mdadm -E /dev/sdc1 
Lots of info but looks normal...
mdadm -E /dev/sdd1 
Lots of info but looks normal...
mdadm -E /dev/sde1 
Lots of info but looks normal...
mdadm -E /dev/sdf1 
Lots of info but looks normal...
mdadm -E /dev/sdg1 
mdadm: cannot open /dev/sdg1: No such file or directory
Looking for /dev/sdg1 the device is missing.  
Looking for /dev/sdg the device is there and looks correct.  So some how /dev/sdg1 is not there.
fdisk /dev/sdg
p
Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001   fd  Linux raid autodetect
This looks to be correct.
mdadm -E /dev/sdh1 
Lots of info but looks normal...

So for some reason 1 of the disks devices is missing.  Even so I would have expected the RAID to start up in degraded mode which it did not.

I am VERY new to RAID and would like to not lose all of what I have on that RAID5 array.  What would be my next move here?


EDIT

After doing some more investigating I saw this when doing the 
mdadm -E /dev/sdc1 <--- Which is the first drive in the RAID array.

/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5a508d1a:fbc70c23:ced01615:07168f29
  Creation Time : Tue Aug 28 08:29:28 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 2441919680 (2328.80 GiB 2500.53 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 3

    Update Time : Thu Sep 20 13:39:19 2007
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 8017b955 - correct
         Events : 0.324796

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       33        0      active sync   /dev/sdc1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       81        3      active sync   /dev/sdf1
   4     4       8      113        4      active sync   /dev/sdh1
   5     5       8       97        5      active sync   /dev/.static/dev/sdg1

Notice that the very last entry is a /dev/.static/dev/sdg1 what in the heck is that?

No matter it is not working.  Should I try to force-rebuild or something?  I am totally lost on this RAID stuff.

---

### Post by fjgaude on 2007-09-21
Has the array ever worked? Do you mount it in /etc/fstab?

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by tekati on 2007-09-22
Yes the array has worked and I did solve my issue actually.

A few weeks ago I added 2 hard drives to the RAID5 array and did the procedure to grow the array to take advantage of the additional 2 hard drives.  I thought I had rebooted since then but apparently not.  The procedure I used worked flawlessly and the array grew from 1.5TB to 2.5TB doing both hard drives at once no problem.

Well when I rebooted the system weeks later the system lost the array altogether.  Not sure why that one drive /dev/sdg was hosed up like it was but come to find out the /etc/mdadm/mdadm.conf file was still set up to look for 4 drives and not 6 which must have confused it THANKFULLY and just stated that no drives for the array could be located which is an error that really did not explain this one too much.  So to fix the issue I did.

I changed the setting in the mdadm.conf file to 6 drives instead of 4.
I then did a # mdadm -A -s and it then found the array correctly.
I removed the bad drive from the array.
I did a # sfdisk -d /dev/sdc | sfdisk /dev/sdg
The partition table copied over correctly and then I had the dev /dev/sdg1 in place.
So then I just added that drive back to the array and walla it rebuilt itself back to normal.  Subsequent reboots worked perfectly.

It was definitely a hair puller on this one.  I could find nothing to even point me in the right direction on google or these forums.  It was by absolute luck that I decided to look for the configuration file and saw the error in there.  Anyway after I set the right drive number in place everything else just came together.

---

### Post by fjgaude on 2007-09-22
I'm sure glad you found your troubles and were able to set things right.

The mdadm.conf file seems important. I can't remember how mine got built but it does show the three drives I have in my raid5 array, but as dev/sdb,c,d1 but sda,b,c1 are usually mounted. I guess because the array has the correct UUID all goes well, at least it has for many months.

Now I wonder when one of the drives breaks how will I know which of the three physically it is? I've asked that question here twice without any responses. <smile>

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

