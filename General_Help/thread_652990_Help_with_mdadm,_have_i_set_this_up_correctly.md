---
title: "Help with mdadm, have i set this up correctly?"
date: 2007-12-29
forum: General Help
---

### Post by krelkor on 2007-12-29
Hi guys

I just started using linux last night, and after tons of trouble with permissions(im not used to not having full administrative rights!) i think ive managed to setup my raid 5 correctly

4x320gigs in raid 5 gives me around 835g usable

I managed to edit my fstab file to include:
/dev/md0 /home/steve/data ext3 defaults 0 2
sudo chmod 777 /home/steve/data

From what ive read, this should mount my drive at the above location(it does, after multiple reboots) and should give me root permissions on the mount point

A problem that occured during the creation was that i couldnt edit /etc/mdadm/mdadm.conf
There was no way i could get permission to edit the file. After some digging on google i thought i found a solution in using:
sudo bash -c "mdadm --detail --scan >> /etc/mdadm/mdadm.conf

this would not return permission denied, but the file does not seem to have anything of importance in it. 

I tried to fail and remove a drive, which seemed to have been ok
I then ran --add /dev/md0 /dev/sda1(the drive i failed) and it seemed to have been added ok. 


Ok, that is all the background to what i have done. My questions are:

 Is the array setup correctly? If i --fail and --remove /dev/sda1 and then --add /dev/sda1 back, should the add be instant? or should it try to rebuild something, in my case it was instant. 

What is the importance of mdadm.conf? I have tried to edit it but i cant seem to get any information into it. I can reboot just fine and the array auto mounts with permissions set in fstab, so am i OK?

Is my fstab setup correctly?

Is it ok to mount the array at its current location of /home/steve/data? Will this mount point cause me problems in the future when i try to upgrade 7.10 to the next version?

Is this array going to cause me troubles in the future? I want this array to be setup now to be 100% future proof in that i can fail out drives, add in new drives, increase the size and grow it without having to worry about not setting up something in the initial installation wrong. 

Any suggestions?

Thanks guys!!!!!!!!

---

### Post by fjgaude on 2007-12-29
Everything you posted seems okay... you have to learn about permissions. Two things now, 1) are you using Gnome, 2) what does this command show?

```
sudo mdadm -D /dev/md0
```

Will get back with you as time permits.

---

### Post by krelkor on 2007-12-29
Hi, thanks for the reply

I am using gnome.
Here is the ouput:


/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Dec 28 20:23:18 2007
     Raid Level : raid5
     Array Size : 937705728 (894.27 GiB 960.21 GB)
  Used Dev Size : 312568576 (298.09 GiB 320.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Dec 29 19:45:45 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f40fa551:0c14e302:01f9e43d:ac30fbff (local to host server)
         Events : 0.4936

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1


I successfully failed, removed, and re-added back a drive. It took 90 minutes at 55MB/S so i think that is ok

Is me mounting it to /home/steve/data going to cause problems if i reinstall ubuntu or upgrade?(i have a seperate OS drive)

---

### Post by fjgaude on 2007-12-29
> **krelkor said:**
> 
Is my mounting it to /home/steve/data going to cause problems if i reinstall ubuntu or upgrade?(i have a seperate OS drive)

Everything is correct. I would mount it to /home, period: /home/data

You will have no trouble with updates or upgrades. The array will stay intact, even if you moved to another motherboard and the like. You just have to have mdadm installed for it to assemble again automatically. You know how to place a line in fstab for it to come up at boot time?

Since you use Gnome you can use natilus scripts to get you into sudo gedit quickly. Place these attached  items in /home/steve/.gnome2/nautilus-scripts. Then when you right-click anywhere, on the desktop, or within programs you can click Scripts and then you are into either gedit or nautlis. From there you can access Permissions as root and change them to steve, as you like.

Do a google on nautilus-scripts to get the scripts.

---

### Post by mmmFiesty on 2008-01-12
I'm having a similar problem and hoped you could help out.

I have a ide OS drive, then 5 sata drives raided together.  I followed the how to over at
[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

A quick recap of the commands I used:
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=5 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
sudo mke2fs -j /dev/md0

entered this into fstab, though the 0 and 3 are not explained...
/dev/md0 /var/media auto defaults 0 3

Then ran a 
mount /dev/md0

After doing all of that, I copied a file over and things seemed good.  Rebooted and it appeared to come up fine.  Turned the server off for the night and came back to it today and things were messed up.  It wouldn't see the raid though the drives were there

My output is similar but a little different

/dev/md0:
Version : 00.90.03
Creation Time : Fri Jan 11 14:44:55 2008
Raid Level : raid5
Array Size : 1562802688 (1490.40 GiB)
Used Dev Size : 390700672 (372.60 GiB 400.08 GB)
Raid Devices : 5
**Total Devices : 4**
Preferred Minor : 0
Persistence : Superblock is persistent

Update Time : Sat Jan 12 15:59:32 2008
State : clean**, degraded**
Active Devices : 4
Working Devices : 4
Failed Devices : 0
Spare Devices : 0

Layout : left-symmetric
Chunk Size : 64K

UUID : b7600d25:fefd0799:6561f3f2:b5fa1b5e 
Events : 0.32

Number Major Minor RaidDevice State
0 8 1 0 active sync /dev/sda1
1 8 17 1 active sync /dev/sdb1
2 8 33 2 active sync /dev/sdc1
3 8 49 3 active sync /dev/sdd1
**4 0 0 4 removed /dev/sde1**


Any idea why that last drive is not showing up?  In addition, when I went into the partition manager, it said something about the superblock being corrupted.  I tried the suggested command 
e2fsck -b 98304 /dev/md0 
but still didn't have any luck.  I'm willing to start over, but just want to make sure I don't make the same mistake again.

---

### Post by fjgaude on 2008-01-12
I don't see that anything was done in error.

I don't understand the e2fsck -b 98304 /dev/md0 you did. The 98304 is at the superblock backup point? You determined this with a file check?

The "3" in the fstab should be a "2" and means the file will be checked after 30 or so startups.

The lost drive, sde1, did you try to reassemble the array using:

```
sudo mdadm --assemble --scan
```

If this doesn't work, do:

```
sudo mdadm --assemble /dev/md0
```

You might have to zero the superblocks and start over if that 98304 wasn't correct. I remember to check where the superblocks are to use:

```
sudo dumpe2fs /dev/sda3 | grep -i superblock
```

Zero superblocks and start over:

sudo mdadm --zero-superblock /dev/sd[nn]

Let us know how you are doing... we don't know everything, we just try to help with what we might know. <smile>

The hot ticket for learning mdadm is at this site, better than the man pages:

[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

---

### Post by mmmFiesty on 2008-01-12
hmmm, not having the best of luck.  First, I got the 98304 number from the output from the initial creation that I saved to a text file, and the command you supplied confirmed the number.

I tried the --assemble --scan and the --assemble /dev/md0 commands but kept getting stopped because it says /dev/md0 is already active and it cant assemble it.  Got the same error when I tried to just recreate it.  

I tried mdadm --stop /dev/md0 but it failed, saying the device or resource is busy.

I wound up removing the entry from fstab, rebooting, stopping the raid and reissuing the create command.  Its now processing and should take about 6 hours.  I'll let you know in the morning if it was successful.  Would you agree with the commands I posted earlier, or suggest something different? - other then using 2 instead of 3 in fstab

I've seen some stuff about raidtab - is there anything I need to do or know about this?  

Finally, while I don't want it to happen, are there any tutorials about what commands need to be issued when a drive dies and is replaced?  Just want to get ahead of the game.

Thanks for your help!

---

### Post by fjgaude on 2008-01-13
Well, the only things I do, suggest is run this command when you think something is wrong:

```
sudo mdadm --detail --test --scan
```

Mine looks like this when everything is correctly running:

> ARRAY /dev/md32 level=raid5 num-devices=3 spares=1 UUID=9e917be3:365b3aef:a0f8169b:995327f7

Study the man page site:

[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

And an example:

[http://www.networknewz.com/2003/0113.html](http://www.networknewz.com/2003/0113.html)

Use search to get the topic of interest. A failed drive in a raid5 array can be removed and replaced with the Manage Mode. The array will without you doing anything continue to work and rebuild itself using the available drives remaining if one fails.

To take a drive out you have to manually fail it like so:

```
mdadm /dev/md0 -f /dev/hda1 -r /dev/hda1 -a /dev/hda1
```
      will firstly mark /dev/hda1 as faulty in /dev/md0 and will then  remove
      it  from the array and finally add it back in as a spare.  However only
      one md array can be affected by a single command.

It simply takes time to understand all the things that are possible. We learn daily...

---

### Post by mmmFiesty on 2008-01-19
Well its me again, and I'm still having trouble.  Everything seemed to work great for the last week, even rebooted the machine a couple of times since then.  Seems like I just cant use this thing over the weekend :mad:
So after loading up a couple hundred gigs on the raid over the last few days, when I restarted it this morning the raid didn't come up again.  Rebooted and still have the same issue.

I'm rather confused as the thing says that it can't recreate the array as it only has 4 disks, yet when I fdisk it show all 5, sda through sde.  Here is the output - going to read some more from those links you sent, but just wanted to see if any of this means anything to you.

I never bothered the check this prior to the failure, but when I ran the partition manager, it said the filesystem was unknown as opposed to ex3.  Though I don't know if it registerd when actually working
# mdadm --detail --scan
mdadm: md device /dev/md0 does not appear to be active.
# mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active.


# mdadm --assemble --scan
mdadm: /dev/md0 assembled from 4 drives - not enough to start the array while not clean - consider --force.
# mdadm --assemble /dev/md0
mdadm: /dev/md0 assembled from 4 drives - not enough to start the array while not clean - consider --force.


# fdisk -l

[PHP]Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30026   241183813+  83  Linux
/dev/hda2           30027       30401     3012187+   5  Extended
/dev/hda5           30027       30401     3012156   82  Linux swap / Solaris

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48640   390700768+  fd  Linux raid autodetect

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48640   390700768+  fd  Linux raid autodetect

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48640   390700768+  fd  Linux raid autodetect

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       48640   390700768+  fd  Linux raid autodetect[/PHP]

---

### Post by mmmFiesty on 2008-01-19
Just a little more info, I ran mdadm --examine /dev/sda1 through /sde1 and a-d all looked the same

[PHP]
# mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.

# mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5bf7f731:49d647f0:b0f64262:4c1be688
  Creation Time : Sat Jan 12 21:26:21 2008
     Raid Level : raid5
  Used Dev Size : 390700672 (372.60 GiB 400.08 GB)
     Array Size : 1562802688 (1490.40 GiB 1600.31 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Jan 17 23:21:07 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : f27045c8 - correct
         Events : 0.6444

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       0        0        4      faulty removed[/PHP]


But when run on sde it seems to indicate that the drive is working and is active, but not clean.  Not sure what that means.

[PHP]# mdadm --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 5bf7f731:49d647f0:b0f64262:4c1be688
  Creation Time : Sat Jan 12 21:26:21 2008
     Raid Level : raid5
  Used Dev Size : 390700672 (372.60 GiB 400.08 GB)
     Array Size : 1562802688 (1490.40 GiB 1600.31 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Jan 17 18:37:04 2008
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f26fd0e6 - correct
         Events : 0.5

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       65        4      active sync   /dev/sde1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       65        4      active sync   /dev/sde1
[/PHP]

---

### Post by fjgaude on 2008-01-19
Perhaps you did something to stop the array from building the first time you created it. Can you remember if you used something like sudo watch cat /proc/mdstat when the building started?

I can see nothing wrong with the data you post, so the array should assemble.

What does your /etc/mdadm/mdadm.conf file look like?

---

### Post by mmmFiesty on 2008-01-19
well I've installed SMART tools on my machine and ran a check to see if there were any errors

```
# smartctl -l error /dev/sde
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
ATA Error Count: 1
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 1 occurred at disk power-on lifetime: 3683 hours (153 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 5f e0 2a 82 e0  Error: ICRC, ABRT 95 sectors at LBA = 0x00822ae0 = 8530656

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 70 cf 2a 82 e0 00      00:15:01.472  READ DMA EXT
  35 00 08 bf 2a 82 e0 00      00:15:01.478  WRITE DMA EXT
  35 00 78 47 2a 82 e0 00      00:15:01.478  WRITE DMA EXT
  35 00 08 3f 2a 82 e0 00      00:15:01.478  WRITE DMA EXT
  35 00 80 bf 29 82 e0 00      00:15:01.477  WRITE DMA EXT

```

Seeing there was an error - though I don't know how to interpret it, I ran a long test - smartctl -t long /dev/sde

```
# smartctl -l selftest /dev/sde
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      3696         -
# 2  Short offline       Completed without error       00%      3693         -
# 3  Short offline       Completed without error       00%      3693         -
```

But it doesn't show any errors there.  Here is  the config file:

# cat /etc/mdadm/mdadm.conf 
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=5 UUID=5bf7f731:49d647f0:b0f64262:4c1be68

I know I did a cat /proc/mdstat to make sure it was running, but don't know if I ran the watch.  If I had it up, it would have only been for a minute or two since I didn't want to waste resources while it was building.

Not sure if the error that is showing up is the death sentence for the drive, or if its repairable, but I'd rather not have the thing messing up my array every week.  Not sure what route to take.

---

### Post by fjgaude on 2008-01-20
Well, I can't say what might be the problem... you can try repairing the drive using this command:

```
sudo e2fsck -C0 -p -f -v /dev/sd[nn]
```

Check the man pages first to make sure I have the options correct.

---

### Post by mmmFiesty on 2008-01-20
Well I wasn't able to use the command as it kept going on about a bad superblock.  The supplied command to restore the superblock also failed.

I just ordered a pair of new drives online and will replace the cable going to the sde drive later this week.  Once I replace sde and get the raid back up, I think I'll pull everything off, kill the raid and make a new raid 5 with a hot spare - is that called raid 6 or is that something different?

Thanks for your help, and I'll let you know how it goes.

---

### Post by fjgaude on 2008-01-20
Okay. raid 6 has double redundancy with up to two hot spares. Take a look here:

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Full of info on raid and all the issues, possibilities.

Let us know how you do when you receate with the new drives.

---

