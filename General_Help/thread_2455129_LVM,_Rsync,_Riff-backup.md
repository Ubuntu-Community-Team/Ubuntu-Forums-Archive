---
title: "LVM, Rsync, Riff-backup"
date: 2020-12-13
forum: General Help
---

### Post by Quarkrad on 2020-12-13
Renewing HD and other bits and thinking of moving towards an LVM install as I can see the advantages to my way of working.  At the moment I use a combination of rdiff-backup (for /home) and gadmin rsync (for unchanging data) for my Backup(s).  What I am unsure about, and yet to find any detail on, is how one uses rdiff-backup and rsync re LVM - this is because I'm not how LVM 'partitions' are named and whether rdiff-b and rsync can 'see' them.  For example, up to now I have used gadmin rsync to manage my non-changing data partitions/folders - would gadmin rsync be able to 'see' LVM partitions the same as non-LVM file structure?

---

### Post by Dennis N on 2020-12-13
With a LVM system involved, you are still working from source folder to destination folder. In grsync, I recall you select them with the OS file chooser. If the OS running Grsync is an LVM install, then it's file chooser is already capable of seeing folders in a mounted LVM logical volume's file system. If the OS is a standard install, you may need to install lvm2 package for the OS to see and use them.

---

### Post by TheFu on 2020-12-13
There's a two-episode video from cat5.tv on using lvm + rdiff-backup that might be helpful. Sorry, I don't recall the exact episode numbers. Also sorry that the "show" is 80% fluff.  They re-cut the show into Technology TV and there might be 10 mins of just the stuff you want in those. cat5.tv and their youtube channel is the place to look.

I can't recall when or who, but someone else posted their LVM snapshot script + rdiff-backup in these forums in the last 2 yrs.  I didn't like that he used multiple rdiff-backup commands ... each makes a separate "set" - always use 1 per day per system to keep stuff clean.

[LIST=1]
[*]Create LVM snapshots of all the LVs you want to backup.
[*]Mount those snapshots to specific locations, read-only. Ensure those mounted locations are not inside an area that is part of the snapshot.  /mnt/{hostname}/{lv-name} is a reasonable way.
[*]Use rdiff-backup to grab everything in /mnt/{hostname}/
[*]umount the snapshots
[*]Remove any backup sets in your rolling backup sets on the target storage
[*]If you like, keep those snapshots around for 24 hours as a safety thing.
[*]Before the next backup session tomorrow, delete the snapshot LVs.
[/LIST]

Simple.

Before doing the snapshots, I like to capture system information and drop it into a directory, /root/backups/ is that I use, that can help recreate the system or recover from failures like corrupted partition tables, lists of manually installed packages, hardware configurations, LVM configurations, crontabs that aren't in /etc/, etc.  stuff like that. Those files are tiny, but oh-so-helpful when bad things happen.

LVM snapshots are handy when we are doing system upgrades or even just weekly patches too.  With snapshots, we can trivially go back to the system state at that point, which can be very handy when upgrades/patches don't go well. It isn't always about pushing that data to 2nd and 3rd storage locations.

---

