---
title: "[SOLVED] NTFS Ext Drive Problem"
date: 2007-11-14
forum: General Help
---

### Post by slackpipe on 2007-11-14
I have a 500 GB Western Digital External Drive.  I've been forced to leave it as NTFS because i often need to hook it to windows boxes.  I used it yesterday on a laptop to back up some information (using the gutsy gibbon live cd)  Now windows wont recognize the partition.  It beeps like it recognizes a drive is connected and the safely remove hardware icon appears.  When i click on it it says "safely remove usb mass storage device" but a drive letter does not appear.  The administrative tools shows the drive as "unhealthy partition" (or something to that effect)  Once it even started a wizard to format the drive.  But in Ubuntu the drive is recognized fine.  I can view the videos off of it, look at the pics, play the music, etc etc etc.  I really need to get it recognized in windows tho.  Is there any tool in Ubuntu that can analyze the drive and see what could be wrong with the partition?  I've looked around, and I believe ntfsfix might do it.  But i wanted some recommendations before i tried anything on the drive and risked hosing it.  Thanks for any help, and my apologies for mentioning windows so much.  ;)

---

### Post by Nameless_one on 2007-11-14
For after you fix it, you might want to check [this](http://www.fs-driver.org/) out. It makes Windows interact with ext2 partitions. I have been using it for a long time and there were never any problems. I'm not sure ntfs-3g is that stable, I suppose that is to blame for the disk not being recognized in WinXP.

---

### Post by slackpipe on 2007-11-14
I have to use the drive on computers that i'm unable to install software on.  I REALLY need it to be ntfs.  What I can't understand is why it works PERFECTLY under ubuntu, but Windows can't read it at all.  I tried ntfsfix and repairing it with gparted.  Both ran fine, but neither fixed the problem.  Anybody got any ideas?

---

### Post by slackpipe on 2007-11-27
Meant to post this a week ago.  Fixed the problem.  I'm not entirely clear on this, but apparently when i shut down the laptop it trashed the partition table on the external.  I found a page somewhere that said something about Ubuntu just looking at the partitions and knowing them and Windows relying on the partition table to get the info.  If anybody knows anything about this, a little clarification would be appreciated.

But what i do know for sure is I unmounted the drive, ran parted, switched the units to GB and then typed RESCUE 0 501.  It found the NTFS partition, rebuilt the partition table and the drive instantly remounted.  It's worked like a charm ever since.

---

