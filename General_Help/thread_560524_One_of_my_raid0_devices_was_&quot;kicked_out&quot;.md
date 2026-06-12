---
title: "One of my raid0 devices was &quot;kicked out&quot;"
date: 2007-09-26
forum: General Help
---

### Post by JimGvo on 2007-09-26
I received an email that stated:  (in part)

A DegradedArray event had been detected on md device /dev/md0.

After examining the /proc/mdstat file, I found:

md0 : active raid1 hda5[1]
      93771264 blocks [2/1] [_U]
But it should also have included /dev/hdb5.  When I attempted to readd it with mdadm it failed telling me "Resource busy" on /dev/hdb5.   I did an fsof on /dev/hdb5 but it didn't show anything.  I then umounted /dev/md0 and tried again.  Same problem.  I googled for and found a number of other suggestions using mdadm but none of them worked, all failed with the resource busy.  I booted single user and attempted the same operation, but again, all I got was resource busy.  
I booted a ubuntu cd and was able to fsck -f /dev/hdb5 and it's fine.  And the best I can tell it seems like it should be a part of the raid device:

[FONT="Courier New"]/dev/hdb5:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : d01d66b4:16efa6c2:d7493088:59f3fe68
  Creation Time : Fri Feb 23 15:03:40 2007
     Raid Level : raid1
    Device Size : 93771264 (89.43 GiB 96.02 GB)
     Array Size : 93771264 (89.43 GiB 96.02 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Sep 16 07:35:53 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 53d8c033 - correct
         Events : 0.4


      Number   Major   Minor   RaidDevice State
this     0       3       69        0      active sync   /dev/hdb5

   0     0       3       69        0      active sync   /dev/hdb5
   1     1       3        5        1      active sync   /dev/hda5[/FONT]

I found a number of hits in google refering to raidstop, raidadd, etc but those utilities don't appear to be available for Ubuntu.

Can anyone shed some light on the right way to reassemble my raid0 device?

Thanks,
Jim.

---

### Post by fjgaude on 2007-09-26
See thread:   [http://ubuntuforums.org/showthread.php?t=560124&highlight=raid](http://ubuntuforums.org/showthread.php?t=560124&highlight=raid)

Might be of help...

---

### Post by JimGvo on 2007-09-27
That didn't help.  THanks,
Jim.

---

### Post by psychicpanda on 2007-09-27
Ha-ha-harden The **** Up
And Go Back To Windows You Nerd ****

---

### Post by JimGvo on 2007-09-28
Sorry, but I've been running Linux since kernel version 0.12.  Windows isn't my thing.  This is my first attempt at software raid, however.

And thank you for your kind and considerate advice.

Jim.

---

