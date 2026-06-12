---
title: "mdadm"
date: 2008-04-04
forum: General Help
---

### Post by Goobie81 on 2008-04-04
I'm still trying to figure out mdadm's quirks :KS

I have this arrangement:

2x 320 GB (sde1,2, sde1,2) split into 1x20,1x300 

I also have 4x 1TB (sda1, sdb1, sdc1, sdd1)

md0: RAID1 (2x 20GB parts)
md1: RAID 1 (2x 300GB parts)
md2: RAID 5 (4x 1TB parts)

It never seems to remember my sparing arrangement ( i get emails from the monitoring complaining about missing spares). 

Like this:
```
root@phantom:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Apr  3 16:03:50 2008
     Raid Level : raid1
     Array Size : 19326080 (18.43 GiB 19.79 GB)
  Used Dev Size : 19326080 (18.43 GiB 19.79 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Apr  4 16:46:34 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 6d827b24:bcee9966:e368bf24:bd0fce41
         Events : 0.14714

    Number   Major   Minor   RaidDevice State
       0       8       66        0      active sync   /dev/sde2
       1       8       82        1      active sync   /dev/sdf2

```

I i fail, remove and re-add the disks, i get this (which is what i thought was normal)

```

root@phantom:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Thu Apr  3 16:52:02 2008
     Raid Level : raid1
     Array Size : 293137984 (279.56 GiB 300.17 GB)
  Used Dev Size : 293137984 (279.56 GiB 300.17 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Apr  4 16:47:06 2008
          State : clean, degraded, recovering
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 1% complete

           UUID : 5d257240:7e5dccd7:e0e769d9:701357b0 (local to host phantom)
         Events : 0.11220

    Number   Major   Minor   RaidDevice State
       0       8       67        0      active sync   /dev/sde3
       2       8       83        1      spare rebuilding   /dev/sdf3
root@phantom:~# mdadm --detail /dev/md2
/dev/md2:
        Version : 00.90.03
  Creation Time : Sat Mar 29 00:12:11 2008
     Raid Level : raid5
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Fri Apr  4 16:45:51 2008
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 2% complete

           UUID : 1b9beb65:4708fd30:e0e769d9:701357b0 (local to host phantom)
         Events : 0.5796

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       4       8       49        3      spare rebuilding   /dev/sdd1


```

Every time i boot i have to fail, remove and add a drive to have it recognised as a spare.

Is this correct behaviour? Should i expect a different output if a spare is fully sync'd ? (Before i re-added the disks they just said "active sync" and it said Spare devices was 0)

This is my mdadm.conf :

```

DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR duffman
ARRAY /dev/md0 level=raid1 num-devices=2 spares=1 UUID=6d827b24:bcee9966:e368bf24:bd0fce41
ARRAY /dev/md1 level=raid1 num-devices=2 spares=1 UUID=5d257240:7e5dccd7:e0e769d9:701357b0
ARRAY /dev/md2 level=raid5 num-devices=4 spares=1 UUID=1b9beb65:4708fd30:e0e769d9:701357b0


```

---

### Post by fjgaude on 2008-04-04
You are booting off one of the arrays?

I don't see, can't think of anything wrong.

I've never made two arrays from one set of drives. The "(local to host phantom)" statement is new to me.

Wish I had some advice... it is not normal to have this "spare" situation.

Are you using Gutsy?

---

### Post by Goobie81 on 2008-04-04
Yeah it's Gutsy...
md0 -> LVM -> System (/, /var etc)
md1 -> ext3 -> Virtual machines
md2 is for other stuff :KS

After they all sync'd they went back to this:

```

root@phantom:~# mdadm --detail /dev/md[0-2]
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Apr  3 16:03:50 2008
     Raid Level : raid1
     Array Size : 19326080 (18.43 GiB 19.79 GB)
  Used Dev Size : 19326080 (18.43 GiB 19.79 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Apr  5 08:41:37 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 6d827b24:bcee9966:e368bf24:bd0fce41
         Events : 0.18400

    Number   Major   Minor   RaidDevice State
       0       8       66        0      active sync   /dev/sde2
       1       8       82        1      active sync   /dev/sdf2
/dev/md1:
        Version : 00.90.03
  Creation Time : Thu Apr  3 16:52:02 2008
     Raid Level : raid1
     Array Size : 293137984 (279.56 GiB 300.17 GB)
  Used Dev Size : 293137984 (279.56 GiB 300.17 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Apr  5 08:41:34 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 5d257240:7e5dccd7:e0e769d9:701357b0 (local to host phantom)
         Events : 0.17008

    Number   Major   Minor   RaidDevice State
       0       8       67        0      active sync   /dev/sde3
       1       8       83        1      active sync   /dev/sdf3
/dev/md2:
        Version : 00.90.03
  Creation Time : Sat Mar 29 00:12:11 2008
     Raid Level : raid5
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Sat Apr  5 08:38:28 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1b9beb65:4708fd30:e0e769d9:701357b0 (local to host phantom)
         Events : 0.6234

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       3       8       49        3      active sync   /dev/sdd1

```

So i guess this is normal?

---

### Post by fjgaude on 2008-04-04
Gosh, you look like you are home free. Congratulations.

Keep us informed on how you are doing.

---

### Post by Goobie81 on 2008-04-07
ok :) 

after all that, my correct mdadm.conf configuration is (arrays only):

```

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=6d827b24:bcee9966:e368bf24:bd0fce41
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=5d257240:7e5dccd7:e0e769d9:701357b0
ARRAY /dev/md2 level=raid5 num-devices=4 UUID=1b9beb65:4708fd30:e0e769d9:701357b0

```


I took it over to my friends house and copied some stuff over the network, and i got up to 55MB/s which i was pretty happy with (for a 'Desktop' machine - man this stuff has really caught up with the big guns) 

Overnight i left it doing a fsck of the md2 filesystem (that took 71 minutes :))

But yesterday i had a gut wrenching issue. I was busy working away on the machine and i started getting IO errors on the console and bus errors attempting to query mdstat. I had a peek at the syslog and i saw this over and over again: 

```

Apr  7 14:32:20 phantom kernel: [56945.200121] end_request: I/O error, dev sda, sector 396297755
Apr  7 14:32:20 phantom kernel: [56945.200183] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Apr  7 14:32:20 phantom kernel: [56945.200186] end_request: I/O error, dev sdb, sector 396297755
Apr  7 14:32:20 phantom kernel: [56945.200375] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK

```

sda & sdb are the only 2 PATA drives in the system (rest are SATA) which form the md0 and md1 raid arrays.
I was a bit suspicious that both of the PATA drives 'failed' at the same time, so i called BS. I had the system rebooted and it came back 100%. Googling suggested that it might be a hardware/firmware/driver combination bug. If you've come across this please let me know (Gigabyte EP-DS3P mobo, WD 320GB PATA drives).

Other than that, the system is awesome! This is the first time i've installed Ubuntu at home for myself and i am very impressed! (except i had to recompile bash to completely remove that command-not-found thing :))

---

### Post by fjgaude on 2008-04-07
Good to see things are really okay afterall... I don't have a clue as to the earlier errors. Your speed is not that good, if you are using modern drives, like only two years or less older.

Look at my marks:

With new Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz) 2/26/08, fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.36/1.34v:

```
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

Notice the disks reads at 212 MNB/sec. That's a raid5 with four late-model drives running off the MB IDE, PCI-e controllers. Your 55MB/sec are for the PATA raid1, eh?

Let us if you have any issues... we don't know everything just like you: we learn day-by-day.

---

### Post by Goobie81 on 2008-04-07
Hmm.

The md2 array is RAID5, made up of 4 brand new 1TB WD drives ([this one]("http://www.wdc.com/en/products/Products.asp?DriveID=336"))
That 55mb/s was from the Sata drives but over the network - i'm happy with because that speed came from a Vista machine (I'm suprised Vista didn't die transferring at that speed).

However i am now concerned about the hdparm readings. I didn't really think about those speeds, and you're right that's pathetic


Having raid5 + crypt taxes the speed a little bit, but the independant disk speed is still 1/4 that of yours:

```

root@phantom:/vms/# hdparm -Tt /dev/sdd

/dev/sdd:

 Timing cached reads:   6746 MB in  2.00 seconds = 3375.77 MB/sec
 Timing buffered disk reads:  202 MB in  3.01 seconds =  67.21 MB/sec
root@phantom:/vms/# hdparm -Tt /dev/md2

/dev/md2:
 Timing cached reads:   7354 MB in  2.00 seconds = 3680.16 MB/sec
 Timing buffered disk reads:  154 MB in  3.01 seconds =  51.19 MB/sec

```

I wonder why that is the case? 

Perhaps i should look closer in the BIOS settings. Maybe super sata mode is crippled by default or something dumb like that.

---

### Post by fjgaude on 2008-04-07
By the cached througput I know you have a pretty fast CPU and quick RAM. What is the CPU precentage load when you are copying files to/from the raid5. Mine runs at about 15%.

I'm sure that crypto cuts up the load in a big way.

My disk reads can go down to as low as 150MB/sec when there are multiple accesses to the array. This can happen when copying to two or more locations at once. My drives are likely about the same as yours but made by Seagate, the first gereration of the perpendicular-read models. The second generation is just out. They up the throughput from about 70 to 105MB/sec for each drive. It'll be awhile before I upgrade. <smile>

Let us know if you find anything that improves your situation.

---

### Post by Goobie81 on 2008-04-08
Apparantly this is just how these new Green drives are . Everything i've read said these drives have extremely poor performance :( 

Oh well, for my purposes scalability was the important factor, not performance ;)

---

### Post by fjgaude on 2008-04-08
I cannot say that new "green" drives are slow, not by a long shot. The ones just coming on the market called 2nd generation perpendicular read are rated at 105MB/sec sequential read. That's getting up there. The drives are all quiet and run at lower power.

Everything is getting better, even Ubuntu.

---

### Post by Goobie81 on 2008-04-08
Sorry i should have clarified that, i meant to say these new "WD 1TB Green Drives" , i just loosely referred to them as Green drives :)

---

### Post by Goobie81 on 2008-04-20
posted this post in the wrong thread :)

---

### Post by fjgaude on 2008-04-21
How are you keeping these days... I had thought all was okay with your raid setup.

---

### Post by Goobie81 on 2008-04-21
I created a new thread to deal with perf issues, i accidently posted in here instead of that thread, thats why i just deleted it and said "oops wrong thread!" :)

[http://ubuntuforums.org/showthread.php?p=4756274](http://ubuntuforums.org/showthread.php?p=4756274)

---

### Post by obscure_detour on 2008-05-21
Hey, I know this thread is a little old but hoping someone could clarify a few things for me as I'm new to mdadm.  :)  Just got mdadm set up on my new hardy box with 3x 750GB drives in a RAID 5 array.

Here is the detail on the array:
```
root@server-desktop:/home/server# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue May 20 21:24:08 2008
     Raid Level : raid5
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed May 21 01:22:29 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 3460b99b:373d05ed:b33a6fc1:0129fa20
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1

```

Now mind you, I have not mounted the array as of yet.  Simply making sure everything is done correctly.  It being mounted or unmounted wouldn't hinder the speed would it?

```

root@server-desktop:/home/server# hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   1982 MB in  2.00 seconds = 991.22 MB/sec
 Timing buffered disk reads:  516 MB in  3.00 seconds = 171.82 MB/sec

```

Why is the cached reads so low?  That's significantly lower than both of your two tests.

Also, on a side note I was curious once you have the array up and running.  How can you go about creating separate partitions for use as /home, /etc?

Is it best to create separate arrays that are partitioned for this?  Or is it best to use LVM on top of the array?

Thanks,

*obscure detour*

---

### Post by Goobie81 on 2008-05-21
What CPU & RAM does the system have?

Show me the output of "vmstat 2 5"

To answer your question about slicing the disk up, you can either partition the MD device or use it as a PV for LVM. Both ways have their advantages and disadvantages. It depends on what you want to achieve and what options you want to have later on in regards to expanding and growing things. 

Do you think you'll add more disks later on? Will you need to grow filesystems?

In my example, i only had the array for one filesystem so i just slapped an encrypted ext3 FS straight onto the block device - i have used all kinds of arrangements in the past. Down the track when this FS runs out of space i'll have the nerve racking fun of adding another disk to the RAID5 array and then growing the encrypted partition and then the FS. :)

---

