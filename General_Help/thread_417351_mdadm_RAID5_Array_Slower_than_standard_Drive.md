---
title: "mdadm RAID5 Array Slower than standard Drive"
date: 2007-04-21
forum: General Help
---

### Post by Rob_Quads on 2007-04-21
I created a RAID5 array using 4 300GB drives to give me a 900GB partition. Recently I have been doing some networking stats to check my gigabit connection and I am finding that doing work with the RAID array gives me slower performance than a single disk.

Below shows some 500MB transfers which indicated that the RAID array is running slowed than an old IDE Drive

```

5200rpm  20GB IDE  Drive	hda /tmp		transferred 524288000 bytes in 34.109 seconds, 120084.288 Kbps ( 15010.536 KBps).
7200rpm 250GB SATA Drive	sda /video		transferred 524288000 bytes in 27.984 seconds, 146367.393 Kbps ( 18295.924 KBps).	
RAID Array			md0 /raid/temp		transferred 524288000 bytes in 38.250 seconds, 107084.967 Kbps ( 13385.621 KBps).

```

The details of the arrray are

```

/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Mar 24 00:00:31 2007
     Raid Level : raid5
     Array Size : 879108288 (838.38 GiB 900.21 GB)
  Used Dev Size : 293036096 (279.46 GiB 300.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Apr 21 21:18:09 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : d41d20ba:89f42c99:1f9c2965:759ec036
         Events : 0.195016

    Number   Major   Minor   RaidDevice State
       0      33        0        0      active sync   /dev/hde
       1      33       64        1      active sync   /dev/hdf
       2      34       64        2      active sync   /dev/hdh
       3      34        0        3      active sync   /dev/hdg[

```
The array is made up of 4 7200rpm IDE Drives running at ATA/133 (hde)

hdparm -Tt

/dev/sda	Timing buffered disk reads:  112 MB in  3.01 seconds =  37.18 MB/sec
/dev/hda	Timing buffered disk reads:   78 MB in  3.01 seconds =  25.87 MB/sec
/dev/hde	Timing buffered disk reads:  122 MB in  3.02 seconds =  40.45 MB/sec
/dev/md0	Timing buffered disk reads:  124 MB in  3.02 seconds =  41.03 MB/sec


Any ideas why its running so slow?

Something that might be worth mentioning is that all 4 drives are across two channels - Channel1 Primary & Secondary + Channel2 Primary & Secondary

---

### Post by Alterax on 2007-04-21
This seems to point to a question of hardware.

Does your RAID-5 array have a special RAID controller card that does all of the RAID work for you, or are you using standard SATA, IDE, or SCSI controllers and setting up the RAID with the disk partitioner?  (If it came on the motherboard, chances are that it's not a RAID controller, so this would be the case).

If not, I am going to go on a limb and assume that your RAID configuration is built using a SOFTWARE RAID device.  If this is the case, there's going to be a decent amount of overhead since software will have to constantly run, deciding which bits to store on which disc.  Slowdowns would be inevitable.

If this is the case, you may get better results by purchasing a card that has built-in RAID-5 capabilities and using it instead of setting up the RAID array at boot.  The computer would only see it as one device, so it'll make configuration a bit easier too.

I hope this helps.

--Alterax

---

### Post by Rob_Quads on 2007-04-21
This is a software MDADM raid configuration. A hardware option is not viable due to cost. 

Most places I have looked at show that even software raid gives performance increases - even on windows lol

---

### Post by Alterax on 2007-04-21
I just noticed that you had added your configuration at the bottom.  You are definitely running a software RAID.

You may be able to add another IDE controller card (cheap as dirt, $29~$50 US dollars), then set each drive as master, one per IDE channel.  This will give you some performance because only one (master or slave drive) on an IDE channel can be active at any given time, although the IDE channels themselves can work in parallel.  Translating that from gobbledygook, instead of having to go back and forth waiting to write to the different drives, the computer could work with all three simultaneously.  BIG performance boost, especially since you are running RAID

Since the card will come with two additional IDE channels, I'd recommend finding a small hard drive to put on that fourth one as your swap space, for even more of a performance boost.  A 5-gig drive would probably be more than sufficient, so it wouldn't be all that expensive.

Will take some reconfiguring (may be easiest to back up data, reconfigure drives, then reinstall), but it will be well worth it.

Good luck!

--Alterax

---

### Post by Rob_Quads on 2007-04-21
After checking my case I don't have any spare PCI slots. Hopefully I will upgrade the base of the server to one with more potential but I have to make do with what I currently have.

---

