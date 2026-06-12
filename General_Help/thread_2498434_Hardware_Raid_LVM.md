---
title: "Hardware Raid LVM"
date: 2024-06-13
forum: General Help
---

### Post by jkillian on 2024-06-13
Im running a Dell Poweredge r710 with a perc-6i raid card. Four identical drives with a total of 22TB in a raid0. No data on the drives outside of the OS yet. That will be backed up on an independent backup drive nightly. I need to make an image of everything configured in rescuezilla for fast restoral. If I just make the image it’s gonna take a week to image and probably waste a ton of space. Im trying to shrink the partition to say 20gig however rescuezilla/clonezilla/gparted isnot gonna let me do it. Even if it’s unmounted it’s not letting me shrink it so…. Ive been told that you can expand lvm xfs but not shrink it. 
New solution if it will work. Disable the four drives from the raid. Re-install ubuntu server with a 20g allotment on just one drive. Configure it and image it. Wipe everything and put the drives all back into the hardware raid at raid0. Use rescuezilla and lay down the image on the new raid0 then expand the partition to use the whole raid. 
Will this work??

---

### Post by TheFu on 2024-06-13
I don't know.

HW-RAID is completely separate from LVM.  LVM provides software-RAID by accessing the disks as JBOD.  If you want to put LVM over any other RAID and not use LVM's built-in RAID, then LVM would just need to be told which disk device (I'd assume it would be RAID) to use as the PV.

I don't see how this can be used to make for a fast restore after a hardware failure beyond what RAID would already handle - or if you need to move everything to a new system.  At some point, the backups need to be pulled from the system and written to other media that is external or on a system connected to the backup network somehow.

XFS cannot be shrunk.  EXT4 can.  Further, EXT4 and LVM are designed to work together, so when resizing the file system along with resizing an LV is needed, we don't need to run 2 commands, just use the    **--resizefs**   option in the command and LVM will handle it - bigger or smaller.

You may want to consider using **pvmove** as a restore method, but I've only used it as a migration technique.

If you need to backup lots of data, I'd strongly suggest using versioned backups that don't require monthly "full" backups to maintain consistency.  For large amounts of data, ZFS is the volume and file system to be used.  Using RAID0 is asking for data loss. If course, everyone needs to learn that lesson the hardware for themselves.  I did and lost 80% of my data because I didn't have backup religion at the time.  It was a bad month, because I still believed there would be some method to get most of the data back, even if only 1 disk in the RAID0 had failed.  Alas, using stripes to get the extra performance also makes all the data gone, gone, gone, if 1 device has a failure.

---

