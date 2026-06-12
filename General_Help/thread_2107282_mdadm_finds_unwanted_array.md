---
title: "mdadm finds unwanted array"
date: 2013-01-21
forum: General Help
---

### Post by Brad22 on 2013-01-21
mdadm insists on installing an array I do not intend.. 

I have set up a raid5 array (call it MD0) with 5 1TB drives (sdb...sdf). This replaces an older array on the same box - couple of new drives, and new array hardware.  I set up the array with no trouble, it works fine.  The best news is, since this was a hardware upgrade project, I have a backup of the data.  

I went through standard mdadm processes to remove the old array, and build new one.  While it works fine after I build it, if I reboot, mdadm never finds the new array - it always finds something else - typically calls it /dev/md0/0 which is a pointer, and to a degraded 4 disk array, not the 5 disks previously set up (all the hardware is OK, I've checked).

I tried all the usual mdadm --stop mdadm --remove, to no avail. Ditto zero superblock.  Ultimately, I removed and purged mdadm. then FDISK and mkfs to wipe the disks.  Rebuilt the array, loaded all the backup data, and thought I was great.  Sooner or later I had to try a reboot - and of course, the bogus array is back, the good one is gone.  I was able to re-assemble the good array since the disk superblocks were correct, and the data was there (after e2fsck).  I've also gotten very specific on the array being local, with a specified name.  SOMETHING is telling mdadm to not do the right array.  

It gets better (worse?) In working with update-initramfs (thinking there's an issue there) I ended up blowing away Unity.  Completely, couldn't get it back. Great.  Backup up critical stuff and reinstall ubuntu.  Go through whole mdadm drill again, and test a reboot.  Now I've got /dev/md127 as a strarted 4 drive array, and /dev/md126 as a inactive 2 drive array. md127 and 126 are default names from linux, it starts at highest value (127) and works backwards. Note - 4 + 2 = 6 drives, I've specified a 5 drive array. The 6th drive was once used early on as a spare, now it is just a blank, unused drive.  

Mdadm clearly has a mind of its own.  None of this is in fstab, I mount this manually.  /etc/mdadm.conf is auto created - changing that affects nothing.  

Any ideas where mdadm gets its ideas from ?

---

### Post by SaturnusDJ on 2013-01-22
What's inside /etc/mdadm/mdadm.conf?
Have a look at [http://ubuntuforums.org/showpost.php?p=10907831&postcount=6](http://ubuntuforums.org/showpost.php?p=10907831&postcount=6)

**If** you've modified the file, run ```
update-initramfs -u
```


Otherwise it may be a possibility the devices aren't ready when they're being assembled.

---

