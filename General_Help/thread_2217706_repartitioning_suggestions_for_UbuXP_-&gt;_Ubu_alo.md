---
title: "repartitioning suggestions for Ubu/XP -&gt; Ubu alone"
date: 2014-04-18
forum: General Help
---

### Post by cecilieaux on 2014-04-18
I'd like some suggestions as to how most effectively and safely "rearrange my furniture," so to speak, as I turn my dual-boot Ubuntu 12.04 LTS / Windows XP machine into simply an Ubuntu 12.04 LTS machine (soon to be Ubuntu 14.04 LTS).

I'm using Ubuntu 12.04 LTS on a Dell Precision 390. My storage space is split into three HDs: 

(1) an 80GB with XP (now no longer internet-connected) where I store the system, applications and their configuration data; 

(2) a 500GB for user data, now split into a Windows data partition and a Linux data partition (/home); the bulk of  my data (music, pictures, the great American novel I've never written, etc.) is on the Windows partition (I kept it there to be accessible to the few XP programs I run since XP cannot "see" Linux Ext3 or 4 partitions, that I know of); the /home Linux partition has newer data and links to the other partition's directories.

(3) and an 80GB Ubuntu 12.04 LTS partition. This obviously evolved from an XP with Ubuntu as an alternate; now with XP dead and my comfort level with Ubuntu at an even level, I think it's worth scrapping XP (I'll keep an XP virtual box going for the declining number of things that *must* be done in XP).

Questions:

a) Is it worthwhile to move Ubuntu (fresh install of 14.04?) from present drive 3 to drive 1 or should I leave well enough alone? 

b) Can an XP partition be a problem when I'm running Ubuntu (will XP malwares migrate from the web and "nest" in the XP partition whence they will cause problems)?

c) Is there are easy way to move the data (150GB or so) from one partition to another, then expand the recipient partition to cover the whole physical drive 2? 

d) Is there a way to guarantee the data doesn't get erase in fresh installs?

e) If this were your machine, what would you do?

Thanks to all in advance, sorry to go on so long.

---

### Post by Impavidus on 2014-04-18
a: A clean install of 14.04 on drive 1 sounds like a good idea. This allows you to dual boot 12.04 and 14.04 for a while. That way you can be sure you have a working system if for whatever reason 14.04 doesn't work at once.
b: The xp partition doesn't pose any dangers to Ubuntu, but without Windows it doesn't serve any purpose. Using ntfs partitions on Ubuntu may give all kinds of little problems. You can't simply execute files, there is no file ownership, more complicated to check and repair the file system. 'Tis best to move over to Linux partitions only.
c: You can copy data using rsync and change partitions using gparted from a live disk. I get the impression that your NTFS partition on the 500GB drive lies to the left of the Ubuntu partition, so that would mean moving all data from the ntfs partition to the Ubuntu partitions (slow), deleting the ntfs partition (fast) and expanding the Ubuntu partition to the left (slow). That would take a lot of time and many things can go wrong.
d: The best way to guarantee you don't loose data is by making backups on an external drive.

e: I would backup everything from the 500GB drive, or at least the Windows partition. Format the Windows partition on drive 2 as ext4. Install Ubuntu 14.04 on drive 1, using the new ext4 partition on drive 2 as /home partition. You can then dual boot 14.04 and 12.04.
If you're happy with 14.04, you can copy your files from 12.04's home partition to 14.04's home partition. Best to have backups on an external drive too. Then you can either repurpose 12.04's home partition to any general storage function and mount it wherever you like, or use gparted on a live disk to delete 12.04's home partition and expand 14.04's home partition to the right. Also wipe drive 3 and mount it somewhere useful.
If your ntfs partition on drive 2 lies to the right of the ext4 partition I would install 14.04 with no separate /home partition. When happy, delete Ubuntu 12.04, merge the contents of your 14.04 /home directory into 12.04's home partition and mount it as your new 14.04 home partition, delete the ntfs partition and expand the new 14.04 /home partition to the right. Again, you can also create a separate partition for storage. Expanding partitions to the right is supposed to work fast and be relatively safe.

---

### Post by cecilieaux on 2014-04-18
Wow! Very thoughtful. Just peeking at it at work, where I can't do any of this. But it's got my wheels turning. I may have some questions as I think about it. I just wanted to express my appreciation.

---

