---
title: "does lvm ditribute data accross physical volumes?"
date: 2008-07-05
forum: General Help
---

### Post by nix4me on 2008-07-05
I am about to setup a lvm volume and want to clarify something.  If I have 4 hard drives, and I create a volumegroup containing all 4 and mount to /home/fileserver.... When i write data to /home/fileserver, does the data get distributed across all 4 drives?

nix4me

---

### Post by bluepowder7 on 2008-07-05
are you asking if it'll split up the file into 4 pieces and write each piece on a separate drive in hopes of minimizing hard drive failure consequences?  or are you asking because you might want to later on break apart the group and would prefer files to never span 2 or more drives?

honestly, in either case, i don't know - i currently have 4 hard drives set up at a LVM group, and i haven't got a clue how to even check which physical drive has which file, and if it has the entire file or if it got fragmented.

if someone knows of a command, i could check it on my system since i've already used up over 900G of my 1.1TB space.

---

### Post by sdennie on 2008-07-05
It depends entirely on how you setup the LVM group.  Have a look at the lvcreate man page.  You can setup LVM to act like RAID0, RAID1 (or JBOD?).  I actually really recommend setting up a RAID array (with 4 disks, RAID5 is nice) and then putting LVM on top of that.  It sounds complicated but, it allows for data redundancy, good performance and all the benefits of LVM.

---

### Post by nix4me on 2008-07-06
I am staying away from raid becuase I have different sized drives.  I have 2 500gig drives and 2 750gig drives.  LVM seemed the best way for me.  I will take a look at the manpage to see how the files get written across the volume.

---

### Post by sdennie on 2008-07-06
> **nix4me said:**
> I am staying away from raid becuase I have different sized drives.  I have 2 500gig drives and 2 750gig drives.  LVM seemed the best way for me.  I will take a look at the manpage to see how the files get written across the volume.

Actually, if you use software RAID, it works on partitions and not disks.  You could potentially create a 500G partition on all the disks and set them up as RAID5 and then take the extra two 250G and set them as RAID1 (if you want redundancy) and even add that array to the same LVM group.  Many possibilities exists.

---

### Post by fjgaude on 2008-07-06
> **vor said:**
> Actually, if you use software RAID, it works on partitions and not disks.  You could potentially create a 500G partition on all the disks and set them up as RAID5 and then take the extra two 250G and set them as RAID1 (if you want redundancy) and even add that array to the same LVM group.  Many possibilities exists.

Yes, certainly would work, but it is highly recommended that you have **full backups** for all important data... working with raid can be a complex experience when things go wrong, removing bad drives, adding drives, resync, etc. <smile>

---

### Post by sdennie on 2008-07-06
> **fjgaude said:**
> Yes, certainly would work, but it is highly recommended that you have **full backups** for all important data... working with raid can be a complex experience when things go wrong, removing bad drives, adding drives, resync, etc. <smile>

There is no doubt that RAID can be a bit complex.  Using LVM with RAID is more complicated than just plain LVM but primarily because of one of the characteristics of using a non-mirrored LVM: When a disk dies, so does all of your data.  That makes it much clearer what to do in the case of a disk failure (wish you had full backups, reformat all the disks and remember to use RAID this time).  ;)

---

### Post by nix4me on 2008-07-06
So I would use the following:

raid 5 - 4 500gig partitions (1.5 terrabyte usable storage)
rait 1 - 2 250gig partitions (250gig usable storage)

Then load lvm and have 1 volume group and 1 logical volume?  This is where I get lost.  How would i know where the data is going (raid  5 or raid 1) or would i care?

If this was setup, and a 750gig drive died, i would loose nothing right?  I could rebuild the array and lvm?

---

### Post by sdennie on 2008-07-06
> **nix4me said:**
> So I would use the following:

raid 5 - 4 500gig partitions (1.5 terrabyte usable storage)
rait 1 - 2 250gig partitions (250gig usable storage)

Then load lvm and have 1 volume group and 1 logical volume?  This is where I get lost.  How would i know where the data is going (raid  5 or raid 1) or would i care?


You wouldn't know where the data is going but, it doesn't really matter because wherever it goes, it's being stored redundantly in one form or another.  As far as setting up LVM on top of the RAID array, it's going to be a personal preference.  I have a RAID5 array with LVM on top and I set it up with one big LVM volume.  The idea being that I'll eventually buy 4 more disks, RAID5 them and then add them to the same logical volume so it looks like one gigantic disk.

> 
If this was setup, and a 750gig drive died, i would loose nothing right?  I could rebuild the array and lvm?

In the setup you've described, a single disk failure wouldn't cause you to lose any data.  In the event of a disk failure, LVM wouldn't even be aware of it and rebuilding the array should be fairly easy (though, it will take forever with that much disk space).

---

