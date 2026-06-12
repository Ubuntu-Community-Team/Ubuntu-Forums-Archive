---
title: "mdadm - replacing 5 yr old drives with new ones, ran into a hiccup"
date: 2014-08-26
forum: General Help
---

### Post by megadave on 2014-08-26
**SOLVED**

I'm an idiot.  Disconnected the wrong old drive.  

Lesson - don't assume.



Hi all:

_Goal:_

Replace the 5 year old disks in my raid1 device, leaving no original disks.

_Setup_

**/dev/md0** is a raid1 device created with mdadm.

it was comprised of two 500 GB drives **/dev/sdb1** **/dev/sdc1**

and it has worked flawlessly for 5 years.

**So far so good**

1.  Purchased two 2TB WD RED drives.
2.  Installed one of the new 2TB drives in, assigned **/dev/sdd1**
3.  added **/dev/sdd1** to **/dev/md0**
4.  used **grow** to grow the array to all 3 disks
5.  **/dev/sdd1** took a little over an hour to sync
6.  All three disks were showing in active sync.

7.  marked **/dev/sdc1 **as fail
8. used remove to remove it from raid
9. used grow to shrink array to 2 disks

mdadm --detail then showed the two disks in active sync, Raid/Total/Active/Working devices showed 2, Failed/Spare 0

**Where it went wrong**

10.  I figured out which physical drive was /dev/sdc by putting it into standby.  
11.  I shut down, disconnected the drive, then booted back up.
12.  No raid. 
13.  I tired to assemble, but mdadm told me** /dev/md0** was not active
13b. the new 2 TB drive had been assigned ** /dev/sdc**, not **/dev/sdd** like it was before
14.  Shut down, hooked up physical drive, reboot.

**As it stands now**

raid now active, working, with ** /dev/sdb1** (one of the original 500GB drives) and **/dev/sdd1** (one of the new 2TB drives)

```
dave@dingo:~$ sudo mdadm --detail /dev/md0
[sudo] password for dave: 
/dev/md0:
        Version : 0.90
  Creation Time : Thu Aug 27 01:29:13 2009
     Raid Level : raid1
     Array Size : 488383936 (465.76 GiB 500.11 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Aug 26 00:11:13 2014
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : b56c7e8b:bfddb8db:5aaa7503:3e0bbc46 (local to host dingo)
         Events : 0.8812

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1
```

_Help_

I'm assuming that i'm missing a step somewhere.

Anyone have any insight?  Thanks.

---

### Post by yancek on 2014-08-26
I'm not sure I'm understanding the problem but, as I understand it, you need to keep your former 500GB drive (sdc) attached in order to use the new 1TB drive(sdd), is that correct?  I would expect that sdd would change to sdc if you remove the current sdc drive.  This is one reason for using UUIDs in fstab to mount which you can get with blkid command.  I'm not familiar with RAID so I can't give an example.

---

### Post by megadave on 2014-08-26
I figured it may have something to do with drive ID's, but my research showed that aside from /etc/mdadm/mdadm.conf, raid config data was written to a superblock on the actual involved disks.

mdadm.conf just contains a UUID for /dev/md0, not for the involved discs.

Doing some more [reading about uuids and mdadm]("http://unix.stackexchange.com/questions/129497/difference-between-uuid-from-blkid-and-mdadm"), i'm worried that when i created this array, i referred to the /dev/sdXX device names instead of the UUIDs.  Have I shot myself in the foot?

---

