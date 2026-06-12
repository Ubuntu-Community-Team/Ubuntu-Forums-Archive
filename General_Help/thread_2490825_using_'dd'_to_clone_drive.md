---
title: "using 'dd' to clone drive"
date: 2023-09-17
forum: General Help
---

### Post by dekinstoke2 on 2023-09-17
Hi

I recently ran ' sudo dd if=/dev/sda of=/dev/sdb status=progress to clone my existing drive to an external back up drive

Everything seemed to run with no errors but at end of play I had several directories missing on the back up, including /Home

I have a feeling my error was running dd from live system?? - should I boot from Live CD and run it from there?

Or maybe there's another explanation ...

Any help please

---

### Post by TheFu on 2023-09-17
Yes. Running dd (or any similar tool) on a live, changing, file system in multi-user mode is problematic.

a) dd is stupid and often fails over many things that cause people to want to move to new storage.
b) ddrescue is like dd, but will continue after a failure and come back to try and get the data that failed previously. Be certain to use a log file.
c) cloning a drive at the block level makes many assumptions, some may or may not be true.  For example, the native block size needs to match.  a 512b blocksize isn't the same as a 4Kb blocksize.  Beware.  

If you do intend to "clone" the whole drive, know that after the clone finishes, bit storage devices cannot be connected to the same computer at the same time.  The UUIDs will match for the partitions, disks, and file systems. The behavior isn't defined, so it is easiest to disconnect one of the disks immediately after the clone.

If your goal is to create a backup, there are better, more efficient, faster, answers. Just sayin'.  Just because something is possible, that doesn't make it a good idea.

For cloning, yes, both the source and target need to be 100% quiesced.  There are many ways to accomplish it. Not being mounted is usually the easiest.

---

### Post by dekinstoke2 on 2023-09-17
Thanks TheFu

I will try running it from a live CD and see if that works and make sure both drives are unmounted. Thought it might be something to do with that

If you have any recommends for a fool proof bit of backup software I would be grateful

cheers

---

### Post by TheFu on 2023-09-17
> **dekinstoke2 said:**
> Thanks TheFu

I will try running it from a live CD and see if that works and make sure both drives are unmounted. Thought it might be something to do with that

If you have any recommends for a fool proof bit of backup software I would be grateful

cheers

a) use ddrescue, not dd, if you want to clone.  There are good reasons to close.
b) There's no such thing as "fool proof", since dog keeps making bigger fools.  Sometimes I'm the fool.  I have posted perhaps 100x here about backups.  The main thing to know is that if you never test the restore, you don't actually know that the backup is working.

Backups need to have these features:
[LIST]
[*]    Automatic
[*]    Stable / Works Every Time
[*]    Different Storage Media
[*]    Fast
[*]    Efficient
[*]    Secure
[*]    Versioned
[*]    Offsite / Remote
[*]    Restore Tested
[/LIST]

Having versioned backups is really easy, but it seems they aren't fool-proof.  An image/clone can provide 1 method of restore, but maintaining it is so cumbersome that nobody does it often enough.  

I setup a mirror backup solution using rsync around 2000 and didn't automate it.  I thought I'd do it manually every month.  I didn't.  That was too much trouble. For about 3 yrs, I'd run the script perhaps once every 6 months.  Initially, I ran it weekly, but that didn't even last 1 month.  A mirror (file system mirror) gets us about 80% of what we need in good backups and they aren't THAT inefficient.

For just a little more effort than a 1-command rsync for backups, you can get nearly everything from the list above using rdiff-backup.  Versioning is built-in. The first backup takes as long as an rsync backup does, but every version after that is very fast and uses just a tiny bit of storage, since the versions only store compressed, changed, data.  For example, if I'm backing up 10GB of data for a system, then to get 60 days of versioned backups will use about 13GB.  Seems like a bargain to me.  And the backups usually take less than 3 minutes to complete.

Without versioned backups, file corruption can make for a terrible day.

Without using disconnected storage for the backups, malware/crypto-ware can make for a terrible day.

If you just want to backup personal files in a HOME directory and keep it really simple, [Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329) has some examples.  Backups are done daily or weekly and 100% automatic.  After all, we will be doing backups much more often than restores.

Since restores are the most important part, [Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927) explains how to restore. Restores may be needed, once every 2 yrs, so having a little overhead in the restore isn't a terrible thing.  After a few restore tests, you'll be able to restore a system to what you need in about 45 minutes.  It depends on the total amount of data, but if you setup the partitions well, there are clear delineations between the OS and data.  

Just some things to consider.

---

### Post by Impavidus on 2023-09-17
What directories were missing on the backup? Could they be on different filesystems?

If you clone a drive, every partition of the source drive will be cloned to the destination drive, but your OS won't automatically mount them the same way. So if sda had both a root partition and a /home partition, both will be copied to sdb, but the /home on sdb's root partition will appear empty. Maybe that's obvious to you, maybe not.

And sure, don't write to a filesystem while cloning it.

---

