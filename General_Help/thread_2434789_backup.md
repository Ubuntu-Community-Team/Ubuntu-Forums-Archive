---
title: "backup"
date: 2020-01-10
forum: General Help
---

### Post by heap1 on 2020-01-10
Hi,
is there any way how to backup ubuntu system, ie once system / drive fail ... i will be able to restore system on new fresh install... ie all services/httpd/vpn etc will be restored.

I saw timeshift, systemback, debfoster... but still not clear which way/one to pick.

The ubuntu i want to backup is running as VM utilizing bhyve... on zfs... maybe the more easier way is to create snapshots? 


thank you for any hitns.

---

### Post by TheFu on 2020-01-10
Yes. There are hundreds of different methods and probably 50 different tools.  These forums have lots of discussions about backup and recovery. 

ZFS has a zsend capability, but you'll need another system also running zfs to receive the data. Based on the question, I suspect this is beyond something you'd want to set up.

Best to do some research. Look at the many different possible options. Decide which you'd like to know more about and try those out on /etc/ which is tiny and has non-trivial file, directory permissions and a few non-standard files, so it makes for an excellent backup test area.  After doing that, if you still have questions, ask.

Probably want to decide if you want a bit-for-bit clone, a partition level clone, or file-based backups.  The clones have some issues.  The file-based backups have different issues, but can be 1000x more efficient in time and storage. Also, file-based backups can be taken while the system is running, assuming LVM has been used and snapshots are mounted for the backup sources.  I would assume the same is possible with ZFS, but wouldn't know anything about bhyve.

---

### Post by GhX6GZMB on 2020-01-11
My experiences:
I use Timeshift myself, but here are my general experiences (I've also tried Systemback and others):

Making regular backup snapshots on a disk or on a USB drive is no problem, restoring is also completely painless.

**Recovering from a disk crash with subsequent re-installation is a much more complex situation.**

A new installation of the OS (DVD/USB .iso) is no big issue.

But for restoring a backup, the major task is to bring the file systems back to their original status. This means that the newly (re)installed disk partitions must be renamed to their previous UUIDs. Otherwise the restore will fail.

So apart from the backup itself, create a separate copy of /etc/fstab and use this as reference for recreating the file system before restoring.

---

### Post by ra7411 on 2020-01-11
I use qt5-fsarchiver for o/s backup. Fsarchiver is easy to install for terminal use, but getting the qt5- gui set up can be a hassle. Also, most of the gui versions around have poor english wording. "Stored partition" button is actually to store the partition you're backing up. It backs up and restores quickly, and is a good choice to preserve your o/s before updates or any big changes you're going to try. I've used it for a number of restores and it worked. You can backup the o/s "live" - that is, while you're using the computer for work. You can install fsarchiver through Synaptic package mgr, and sometimes synaptic shows qt5-fsarchiver, but how well it actually installs the gui is mixed.

In my opinion, Ubuntu/Conical (whatever) should get the gui and language syntax problems solved and make this a main backup program in the software center.

I use Grsync for incremental backup of user files (/Home). You can get this out of the regular software center.  This also does your backup "live" while you do other work.

---

### Post by VMC on 2020-01-12
That  qt5-fsarchiver is actually better than fsarchiver, even though it used its base. I find the qt version to have better compression and as a gui its the best. It was also hard to configure. I haven't use it in a while though.

---

### Post by TheFu on 2020-01-12
I've used fsarchiver for small partitions that don't change - basically Windows Recovery stuff.
As for running fsarchiver on a live, running, Linux, system - you risk having a corrupt backup unless an LVM snapshot is what gets grabbed. This would be more important for anyone running any DBMS tools.  If you don't do that, the risks are fairly minor.

But why have 2 backup solutions when only 1 is needed? I've always found that confusing.  A good rdiff-backup with 90+ days of versioning covers everything needed with very little storage overhead.

---

