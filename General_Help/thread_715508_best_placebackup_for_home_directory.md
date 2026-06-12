---
title: "best place/backup for home directory?"
date: 2008-03-04
forum: General Help
---

### Post by deltateam2 on 2008-03-04
I've long wondered if the best solution for backing up my ~/ is to mount it via cifs or nfs to my 2tb opensolaris raid-z box or to have ~/ on local disk and rsync'ing incrementally with cron.daily (not complete copies but something like [this]("http://www.mikerubel.org/computers/rsync_snapshots/")).  Anybody have any nifty methods for backing up?

---

### Post by Rocket2DMn on 2008-03-05
Backing up to external hard drives is the preferred method since it is fast and reliable.  I use a program called Simple Backup aka sbackup (available in the repos) to make full and incremental compressed backups of my /home directory + some others.  The program is also capable of doing remote backups since that seems to be up your alley.
Backing up to the same hard disk linux and/or your /home directory is on doesn't make a lot of sense since if the drive crashes, you're screwed.

---

### Post by deltateam2 on 2008-03-07
I'm not merely backing up to the same hard drive.  Raid-Z is a Raid-5-like implementation on the best file system written for unix-like operating systems, zfs.  Zfs is seemingly 10 times more simple then raid5 on linux.

---

### Post by Rocket2DMn on 2008-03-07
I know what RAID-5 and zfs is, but I'm still not entirely sure I understand your question - I'll try and answer it broadly.  Your system will run much faster if your home directory is on your local disk and you make incremental backups to a remote location or external drive - don't keep your home directory on the raid-z system, even though it is "safer".

If you sit in front of your raid-z box and remotely mount your home directory, that won't do anything since the data is still on your original machine, not on the raid-z disks.  I don't think this is what you're asking though.

You can backup your home directory over the network to your raid-z, to some folder somewhere using a program like Simple Backup (which is built on rsync) which is capable of making incremental backups.  Then even your backup is stored on a system that is fail resistant.  If your local hard drive fails, you can fix the problem (either by reinstall or new hard disk, or whatever), and it is easy to reload your backed up home directory which is stored on the raid-z system in a series of compressed archives.

---

