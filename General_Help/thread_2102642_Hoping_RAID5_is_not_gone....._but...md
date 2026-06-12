---
title: "Hoping RAID5 is not gone..... but.."
date: 2013-01-07
forum: General Help
---

### Post by JohnnyC35 on 2013-01-07
I had a RAID5 with 7 drives. One of them was faulty and another was going in and out. I just got a new drive. Booted up the system, and the RAID wont initialize. It's happened before, and all drives are showing online, at least for now.
I have been following [http://www.overclockers.com/forums/showthread.php?t=689300](http://www.overclockers.com/forums/showthread.php?t=689300) as it seems to be a similar issue.

/dev/sdd was showing as no superblock. I tried 
```

sudo mdadm --assemble --scan --force -vmdadm: looking for devices for /dev/md127
mdadm: /dev/sdj has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdi
mdadm: /dev/sdh has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdd5
mdadm: Cannot assemble mbr metadata on /dev/sdd2
mdadm: no recogniseable superblock on /dev/sdd1
mdadm: Cannot assemble mbr metadata on /dev/sdd
mdadm: /dev/sdg has wrong uuid.
mdadm: /dev/sdf1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sde1
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdc1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdf2 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdc2 is identified as a member of /dev/md127, slot 1.
mdadm: /dev/sdb2 is identified as a member of /dev/md127, slot 0.
mdadm: added /dev/sdc2 to /dev/md127 as 1
mdadm: added /dev/sdf2 to /dev/md127 as 2 (possibly out of date)
mdadm: added /dev/sdb2 to /dev/md127 as 0
mdadm: /dev/md127 has been started with 2 drives (out of 3).
mdadm: looking for devices for /dev/md1
mdadm: no recogniseable superblock on /dev/md127
mdadm: no RAID superblock on /dev/sdi
mdadm: no RAID superblock on /dev/sdd5
mdadm: no RAID superblock on /dev/sdd2
mdadm: no RAID superblock on /dev/sdd1
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdf2 has wrong uuid.
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sde1
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdc2 has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb2 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdj is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdh is identified as a member of /dev/md1, slot 7.
mdadm: /dev/sdg is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdf1 is identified as a member of /dev/md1, slot 5.
mdadm: /dev/sdc1 is identified as a member of /dev/md1, slot 6.
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 4.
mdadm: no uptodate device for slot 1 of /dev/md1
mdadm: added /dev/sdj to /dev/md1 as 2
mdadm: no uptodate device for slot 3 of /dev/md1
mdadm: added /dev/sdb1 to /dev/md1 as 4
mdadm: added /dev/sdf1 to /dev/md1 as 5
mdadm: added /dev/sdc1 to /dev/md1 as 6
mdadm: added /dev/sdh to /dev/md1 as 7
mdadm: added /dev/sdg to /dev/md1 as 0
mdadm: /dev/md1 assembled from 5 drives and 1 spare - not enough to start the array.
mdadm: looking for devices for /dev/md1
mdadm: no recogniseable superblock on /dev/md127
mdadm: /dev/sdj is busy - skipping
mdadm: no recogniseable superblock on /dev/sdi
mdadm: /dev/sdh is busy - skipping
mdadm: no recogniseable superblock on /dev/sdd5
mdadm: Cannot assemble mbr metadata on /dev/sdd2
mdadm: no recogniseable superblock on /dev/sdd1
mdadm: Cannot assemble mbr metadata on /dev/sdd
mdadm: /dev/sdg is busy - skipping
mdadm: /dev/sdf2 has wrong uuid.
mdadm: /dev/sdf1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdf
mdadm: no recogniseable superblock on /dev/sde1
mdadm: Cannot assemble mbr metadata on /dev/sde
mdadm: /dev/sdc2 has wrong uuid.
mdadm: /dev/sdc1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdc
mdadm: /dev/sdb2 has wrong uuid.
mdadm: /dev/sdb1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdb
mdadm: Cannot assemble mbr metadata on /dev/sda
john@MEDIA01:~$ sudo mdadm --assemble --scan --force
mdadm: /dev/md127 is already in use.

```

and also
```

john@MEDIA01:~$ sudo mdadm --assemble /dev/md1 /dev/sdj /dev/sdh /dev/sdd /dev/sdg1 /dev/sdc1 /dev/sdb1 --force
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdd has no superblock - assembly aborted

```
examining /dev/sdd gave this info, which didn't seem paticular helpful
```


sudo mdadm --examine /dev/sdd -v
/dev/sdd:
   MBR Magic : aa55
Partition[0] :     14630912 sectors at         2048 (type 83)
Partition[1] :      1026050 sectors at     14635006 (type 05)

```

trying the trick with create rather than assemble has kind of buggered things tho, and I think I am stuck at this point. ... I used create rather than assemble, as it has worked in the past, and it was suggested to work in the link above, as well as some Googling/forums. however now I have a 9Tb array that it says needs formatting. :'(
I don't suppose I can recreate the old array some how? or retrieve any data? even just a directory listing would be great at this point...

here's the info from the create...
```

 sudo mdadm --create /dev/md1 --assume-clean --level=5 --raid-devices=7  /dev/sdj /dev/sdg /dev/sdh /dev/sdi /dev/sdf1 /dev/sdc1 /dev/sdb1
mdadm: /dev/sdj appears to be part of a raid array:
    level=raid5 devices=7 ctime=Mon Jan 24 20:00:46 2011
mdadm: /dev/sdg appears to be part of a raid array:
    level=raid5 devices=7 ctime=Mon Jan 24 20:00:46 2011
mdadm: /dev/sdh appears to be part of a raid array:
    level=raid5 devices=7 ctime=Mon Jan 24 20:00:46 2011
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Mon Jan 24 20:00:46 2011
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Mon Jan 24 20:00:46 2011
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Mon Jan 24 20:00:46 2011
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md1 started.


```

thanks for any help :)

---

### Post by Cheesemill on 2013-01-08
With the damage you've now done by running the create command I would say your best bet is to just to start again with a clean array and restore all of the data from your backup.

---

### Post by Grenage on 2013-01-08
Ah the horrors of the blind leading the blind, when it comes to following forum posts.  To echo Cheesemill - hopefully you have some sort of backup.

---

### Post by SaturnusDJ on 2013-01-09
Looks like the same problem as [http://ubuntuforums.org/showthread.php?t=2102720](http://ubuntuforums.org/showthread.php?t=2102720).

You might have a chance to fix it.

When creating you need to put the drives/partitions in the right order as they where when creating the array for the first time.

You've used --assume-clean, that's good.

The metadata version needs to be the same as the original also.

And if you're leaving the failed drive out you need to put "missing" at the place of that drive's/partition's path.

---

### Post by JohnnyC35 on 2013-03-18
sadly I couldn't get anything back. starting over again

---

### Post by Snaglpuss on 2014-01-25
FakeRaid question #2
now I'm not a total noob but back then I was, started building the first server with 6.10, everything ran fine in 07 then i did an upgrade in place to 7.10 which crashed!! and not having time to mess with it till 08 i found out that out of 4 sata drives @300gb ea sdb failed but that was 6 months after the upgrade failed, related to video problems and ati rage xl issues that weren't solved. prevented it from booting to GUI and left me at intramfs which at the time i didn't understand.

so i tried to replace with another drive thinking rebuild was automatic which it wasn't. not having time since to go into 6 different directions of rebuilding i set the unit aside tho i had just transferred all my nas files over to build a bigger nas when the failure occurred. having finally removed myself from 80 hr work weeks and unbury all the other projects..

I finally got back to this one. after a few checks I found no bootable live versions that would give me video and GUI except 10.10 desktop, which showed a partial array. with that hope, I went to explore mdadm and found no working versions for 10.10 from term. legacy I guess. Since the array booted from the upgrade and died at console I tried and found that mdadm was available from the 7.10 upgrade. ran mdstat found the arrays md1 md2 active md0 inactive except for the failed one md0 then started having other failures after 24hrs of runtime. terminated the machine pulled a sata cable loose and replaced it and others with a new one and found the drives started to work without failure.

since i could not make the new drive work in the array and looked and had no superblock info much less uuids on any of the remaining arrays i figured out my method of madness of my original redundancy plan, created a 4 drive (only had 4 channels) raid 5 and then raid 1 the three internal partitions 1 a boot drive 1 a swap and 1 a data drive. since that time i have put back the original "bad drive" with a new cable and its the only one now with a uuid, date codes, and shows sync when all the rest show as spares and unknown statuses.

reading through all wikis have left me confused on how not to clobber my data by making a wrong mdadm or parted move, from this ver 7.10 mdadm. any help with directional restoration of the original raid and then the secondaries would be great oh and couldn't find an edit tool to even look at mdadm.conf from intramfs, so, what to do?.. i want to transfer that data back once i get this up!

---

