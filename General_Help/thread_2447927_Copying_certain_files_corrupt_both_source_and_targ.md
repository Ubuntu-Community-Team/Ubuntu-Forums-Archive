---
title: "Copying certain files corrupt both source and target  file system"
date: 2020-07-29
forum: General Help
---

### Post by bernadinorad on 2020-07-29
I have a big iso file, splitted into 50+ rar files for easy download.
I have downloaded them in the users Download directory (home fs). Extracted the iso file without any problem - thus the rar files must be ok.

Then I want to copy them into my shared directory "/shared" at the root partition (I have about 25+GB free space at the root partition) and think to borrow a little bit of them. I know if I left very little free space at root partition some problems may appear.

My /tmp is mounted using separate linux swap partition. So I think too little swap space can be omitted here.

Problem:
Each time the copy process reached somefile.r057 an error occured - a splicing problem because read only-, and then BOTH partitions (home and root) become read only.

I can't imagine how easy it is to corrupt a linux (unix) file system. I can understand if the target partition is getting corrupted due to incorrect write process.
But the source partition has become corrupt too...

I've repeated the repair filesystem and copying, to the same exact error... 

Any clues?
Thanks
Bernard

PS: It is a 14.04 32bits toshiba laptop with 3 GB RAM and 500 GB hd

---

### Post by TheFu on 2020-07-29
**14.04 support ended in 2019.  Move to a supported release.**  20.04 is the current LTS release. Probably best to do a fresh install, since it won't be easy to move up from 14.04 at this point. The repos are mostly gone.  Good luck.

There are different Linux file systems. If they are journalled like ext4 or xfs or zfs, it is very difficult to cause corruption.  But no file system can survive when storage hardware is failing. My first assumption would be some sort of hardware issue - bad disk, bad SATA cable, or using an experimental file system.  Check the system log files for errors and warnings about the storage.  Also check SMART data for the storage.  When the OS decides to make a file system read-only, it is protecting the storage from harm as best it can.

Make certain you have excellent backups for any data you don't want to lose. SSDs go read-only just before they fail, BTW.

---

### Post by bernadinorad on 2020-07-30
I am using ext4. I guess you are correct, it could be a sign of hardware failure.

I'll buy a hd replacement and upgrade to, well 20.04 could be a good choice if my hardware has enough power for it.

Thanks anyway

---

