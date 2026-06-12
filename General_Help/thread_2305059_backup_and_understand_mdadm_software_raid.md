---
title: "backup and understand mdadm software raid"
date: 2015-12-02
forum: General Help
---

### Post by Drenriza on 2015-12-02
I have installed a mdadm raid 1 setup to get a better understand of how mdadm works.

[B]md0 (Data)
md1 (Swap)
> md1 : active raid1 sdb2[1] sda2[0]
      4878272 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdb1[1] sda1[0]
      287953728 blocks super 1.2 [2/2] [UU][/B]

But i have a question i can't seem to find an answer to.

What happens with the raid if for example the machine running the raid has a MB crash, and needs a new MB?
[INDENT]Where does the raid setup for the disks live?
[/INDENT]

And how can i backup the mdadm raid configuration, so if i need to i would be able to unplug the disks,
move them to a new machine, "import" the config and continue working on the disks without loosing data.

Hoping for some pointers

Thanks on advance
Kind regards

---

### Post by TheFu on 2015-12-04
TL;DR - /etc/mdadm - you'll want more data than just that however.  
**sudo mdadm  --detail /dev/md1**

RAID has nothing to do with backups. RAID is for HA and/or maybe improved disk performance.

Backups need to capture either a copy of the OS and all files, or enough of the settings that you can recreate the system in some known manner.  There are a few key directories that every Unix Admin knows must be backed up.  /etc/ is one of those.  On "servers", there are many others which are dependent on the software loaded.  If it is a web server, there is likely some stuff under /var/www or /var/html and maybe /opt that needs to be backed up.  If end-users have accounts, then their HOMEs need to be backed up (data, not all the cached/trash junk). RDBMS servers will need their DB files to be backed up - every DBMS has different methods to backup a running DB. Copying the files will likely just lead to corrupted DBs at restore time.

Don't forget to actually test the restore process. The backup process is only 10% of this .... 90% is the restore, after all, that is the entire point of making backups.  And don't fall into the trap of backing up to encrypted backup files, but forgetting to have a copy of the backup key outside the backup set files.  See that a lot.  It is sad, but funny, in a way.  They have backups, but ZERO chance of accessing them because of the encryption used.  Test the restore. Trust me. There will be something forgotten unless an image-based backup is used. The downside for images is that versioned backups are next to impossible and system downtime is required to make the image.

---

### Post by Drenriza on 2015-12-08
> **TheFu said:**
> TL;DR - /etc/mdadm - you'll want more data than just that however.  
**sudo mdadm  --detail /dev/md1**

RAID has nothing to do with backups. RAID is for HA and/or maybe improved disk performance.

Backups need to capture either a copy of the OS and all files, or enough of the settings that you can recreate the system in some known manner.  There are a few key directories that every Unix Admin knows must be backed up.  /etc/ is one of those.  On "servers", there are many others which are dependent on the software loaded.  If it is a web server, there is likely some stuff under /var/www or /var/html and maybe /opt that needs to be backed up.  If end-users have accounts, then their HOMEs need to be backed up (data, not all the cached/trash junk). RDBMS servers will need their DB files to be backed up - every DBMS has different methods to backup a running DB. Copying the files will likely just lead to corrupted DBs at restore time.

Don't forget to actually test the restore process. The backup process is only 10% of this .... 90% is the restore, after all, that is the entire point of making backups.  And don't fall into the trap of backing up to encrypted backup files, but forgetting to have a copy of the backup key outside the backup set files.  See that a lot.  It is sad, but funny, in a way.  They have backups, but ZERO chance of accessing them because of the encryption used.  Test the restore. Trust me. There will be something forgotten unless an image-based backup is used. The downside for images is that versioned backups are next to impossible and system downtime is required to make the image.

Thanks for the reply.

As you state raid is for HA and or better disk throughput.
What i ask is where mdadm saves it software raid configuration for its stripping and such.

So lets say i have a raid 1 setup in a server. This server has a critical hardware fail on **ALL** components _except_ the HDD's which is in perfect working condition.
How would one move the software raid to a new system without loosing what is on the disks?

If for example you have 2x 3TB disks, it would take longer to get the data from a backup than moving the software raid to a new machine (i would reckon).
On decent hardware raid controllers you can make a backup / export of the controller configuration. So in case the controller dies or you need to move to a new machine
you can install a controller and import the configuration, install the disks and continue on working.

---

### Post by mastablasta on 2015-12-08
for starters you should not have RAID0 as it doesn't offer any redundancy in case of disk failure. hence the 0.

otherwise you mount it on new system and it chugs away. I had OS on separate disk and it went bust. debian was on it. then I got a new OS disk, installed Ubuntu on it, mounted the RAID1 array and that was it.

---

### Post by TheFu on 2015-12-08
I've moved a SW-RAID array between different physical systems a few times. Don't recall anything difficult about it. It has been a few years. I think installing mdadm on the new box was about it, then adding the devices to the /etc/fstab.  If it was any more difficult than that, it wasn't much more difficult. Sorta "just worked."  I probably wrote a blog article about how easy it was.  [https://serverfault.com/questions/32709/how-do-i-move-a-linux-software-raid-to-a-new-machine](https://serverfault.com/questions/32709/how-do-i-move-a-linux-software-raid-to-a-new-machine) seems like what you probably need.

HW RAID controllers fail and when that happens, the hunt for an exact replacement is on. That's easier if you spent $300+ for a well-known HBA or if you are a business and pay for 4-to-24 hour hot-spares to be provided by the vendor.  It isn't so easy for a home user.  I've had a $150 RAID card fail and was unable to find a replacement. The "close" replacement I found wasn't compatible, so all the data on those RAID disks were gone.  Had to restore from backups. Thankfully, I had gotten backup religion after loosing 80% of the data by running multi-disk volumes around 2000 - sort like RAID0. Nothing teaches backup religion like data loss. ;(

RAID0 with 2 drives may improve performance, but it also doubles the chances of complete data loss should anything fail in either controller, cables, or disks.  RAID0 is for temporary storage for video editors, but most of those folks will have moved to RAID0 with SSDs by now to get the performance they demand.  *If you already have backup religion with this data, we'll stop hounding you.*

A few blog articles about data and RAID:
* [http://blog.jdpfu.com/2010/02/12/software-raid-migration](http://blog.jdpfu.com/2010/02/12/software-raid-migration) - read the article for background on the RAID migration. Not quite the same as yours, but close.
> So the disk swap worked. All 6 disks were swapped, the machine was booted and the OS came up. ZERO, yes, ZERO issues. The boot drive was found. The backup drive and mount points were found and mounted. The software array controlled by mdadm was found, assembled, mounted and is running. I didn&#8217;t have to do a thing. No change to any configuration. No real special SATA cable locations. The first SATA cable locations worked perfectly. I wasn&#8217;t stupid about the SATA cables, but the drives are definitely not on the devices in the new machine either.
* [http://blog.jdpfu.com/2012/08/20/how-long-do-you-use-hard-drives](http://blog.jdpfu.com/2012/08/20/how-long-do-you-use-hard-drives) - I'm certain there are a few HDDs here from 2008 still spinning.  From my chair today, I can count about 30.

Anyone else wonder whatever happened to their old 240MB HDDs?

---

### Post by Drenriza on 2015-12-09
> **mastablasta said:**
> for starters you should not have RAID0 as it doesn't offer any redundancy in case of disk failure. hence the 0.

otherwise you mount it on new system and it chugs away. I had OS on separate disk and it went bust. debian was on it. then I got a new OS disk, installed Ubuntu on it, mounted the RAID1 array and that was it.

Thanks for the reply.
That was my bad, corrected it to raid 1! :)

---

### Post by Drenriza on 2015-12-09
> **TheFu said:**
> I've moved a SW-RAID array between different physical systems a few times. Don't recall anything difficult about it. It has been a few years. I think installing mdadm on the new box was about it, then adding the devices to the /etc/fstab.  If it was any more difficult than that, it wasn't much more difficult. Sorta "just worked."  I probably wrote a blog article about how easy it was.  [https://serverfault.com/questions/32709/how-do-i-move-a-linux-software-raid-to-a-new-machine](https://serverfault.com/questions/32709/how-do-i-move-a-linux-software-raid-to-a-new-machine) seems like what you probably need.

HW RAID controllers fail and when that happens, the hunt for an exact replacement is on. That's easier if you spent $300+ for a well-known HBA or if you are a business and pay for 4-to-24 hour hot-spares to be provided by the vendor.  It isn't so easy for a home user.  I've had a $150 RAID card fail and was unable to find a replacement. The "close" replacement I found wasn't compatible, so all the data on those RAID disks were gone.  Had to restore from backups. Thankfully, I had gotten backup religion after loosing 80% of the data by running multi-disk volumes around 2000 - sort like RAID0. Nothing teaches backup religion like data loss. ;(

RAID0 with 2 drives may improve performance, but it also doubles the chances of complete data loss should anything fail in either controller, cables, or disks.  RAID0 is for temporary storage for video editors, but most of those folks will have moved to RAID0 with SSDs by now to get the performance they demand.  *If you already have backup religion with this data, we'll stop hounding you.*

A few blog articles about data and RAID:
* [http://blog.jdpfu.com/2010/02/12/software-raid-migration](http://blog.jdpfu.com/2010/02/12/software-raid-migration) - read the article for background on the RAID migration. Not quite the same as yours, but close.

* [http://blog.jdpfu.com/2012/08/20/how-long-do-you-use-hard-drives](http://blog.jdpfu.com/2012/08/20/how-long-do-you-use-hard-drives) - I'm certain there are a few HDDs here from 2008 still spinning.  From my chair today, I can count about 30.

Anyone else wonder whatever happened to their old 240MB HDDs?

Thanks for the detailed reply and own experience!

---

### Post by TheFu on 2015-12-09
Be certain to read the blog article - UUIDs were the main reason it "just worked."

Also, RAID1 isn't a replacement for backups.  I only have RAID1 disks because there are VMs running on that storage.  For things like media, I don't use RAID at all, just weekly backups (media files don't change that often).  For OS and personal files, automatic, daily backups, with versioning are required.  There have been times that only a backup would solve my RAID issues - just sayin'.  **RAID is never a replacement for backups.**  So I'm off my soap box now.

---

