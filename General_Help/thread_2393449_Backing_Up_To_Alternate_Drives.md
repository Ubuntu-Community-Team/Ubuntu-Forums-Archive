---
title: "Backing Up To Alternate Drives?"
date: 2018-06-03
forum: General Help
---

### Post by n5kzw on 2018-06-03
While trying to solve some system issues by upgrading to 18.04, I managed to reformat both my main drive and my USB backup drive.  All data lost because I forgot to disconnect the backup drive.  To avoid this mistake in the future, I would like to use two USB drives and alternate the backup between them.  Is there a way to automate this?  Regards, Ed

---

### Post by TheFu on 2018-06-04
rsync?
I use rdiff-backup for local backups, but using rsync for the backup storage to mirror everything off-site.  You could use rsync to mirror any backups to a 2nd disk/location.

Or most backups storage version information in the backup sets, so if you swap them weekly, you'll end up with 2 backups, 1 week apart.  I bet that would work just as well.  But for any portable devices, be certain you use sufficient encryption to store that sensitive data outside your physical control.  IMHO, all portable devices need to be encrypted. Laptops, smartphones, USB storage.  Anything that can be trivially moved needs full encryption.

---

### Post by Ralph L on 2018-06-04
I use Luckybackup, a front end to rsync, to have 2 separate alternating backups.  I just set up 2 LuckyBackup profiles that are entirely independent of one another.  I alternate running them, so one is always a week older than the other one.  I use fcron to schedule them.  I wrote a little script to run each of them, which asks if the appropriate disk is mounted, before it runs Luckybackup.

---

### Post by TheFu on 2018-06-04
> **Ralph L said:**
> I use Luckybackup, a front end to rsync, to have 2 separate alternating backups.  I just set up 2 LuckyBackup profiles that are entirely independent of one another.  I alternate running them, so one is always a week older than the other one.  I use fcron to schedule them.  I wrote a little script to run each of them, which asks if the appropriate disk is mounted, before it runs Luckybackup.

Good idea to check for the disk being mounted.  I was burned once.

I do it by mounting by labels to specific locations and checking the mtab.  Real mounts update the mtab. Fake mounts don't.  Different labels means a unique identifier can be used for each disk.   Smart idea to take one into another location (like work) every week and swap the backups.

My backup tasks used to mount/umount the backup storage before/after each job. This was a way to prevent accidentally touching the backups without explicitly wanted to.  That was before I switched to networked backups, which changed everything for me.

But there are lots of other methods to accomplish the same things.

Hopefully, some more smart folks will respond with how they do it.

---

