---
title: "backup fails using default deja dup and folder permissions"
date: 2013-10-16
forum: General Help
---

### Post by SirWeazel on 2013-10-16
When running a backup using ubuntu's built in default (deja dup) it fails reading some of the directories in my home folder. It fails because for some reason some of the folders are owned by root.  Why are some of these folders owned by root in my home directory, and should i correct the problem.  I also have another user account where some of the same folders fail because they are also owned by root.  Any help in this issue is much appreciated.

Running default ubuntu 13.04 64bit fully updated with a couple additional programs installed from some .deb files or ppa's.

Folders below that fails and there corresponding current owner.
```
/home/chris/.cache/dconf --- owner is root
/home/chris/.config/enchant --- owner is root
/home/chris/.config/leafpad --- owner is root
/home/chris/.gstreamer-0.10/registry.x86_64.bin --- owner is root
/home/chris/.gvfs --- owner is root

```

---

### Post by TheFu on 2013-10-16
If you've been using GUI programs with sudo (or any equiv), then those directories will be owned by root.
If you've enabled HOME directory encrption, backups will be difficult.
If you are backing up just HOME for 1 user, then using the backup tool as THAT specific user is fine, but if you need/want to backup the entire system, then it must be performed as root to maintain ownership, groups and permissions.

Does this make sense>

Running GUI tools as root - not exactly a best practice.

---

### Post by SirWeazel on 2013-10-18
Makes sense. Thanks. As a follow up...
1. Should i correct the ownership of these files?
2. In the past i would use gksu "graphical application" ... but it appears to not be included in these latest versions.  Is this something i should add, or just stick to command line actions when needed. Its sometimes frustrating because running nautilus as root to navigate and delete/move/change permissions is often more convenient.
3. I'm fine running backups as each user, but it might be useful in the future to run it as root. I tried searching, but ran into some contradictions. What do you think?

Thanks for your help.

---

### Post by TheFu on 2013-10-18
> **SirWeazel said:**
> Makes sense. Thanks. As a follow up...
1. Should i correct the ownership of these files?
2. In the past i would use gksu "graphical application" ... but it appears to not be included in these latest versions.  Is this something i should add, or just stick to command line actions when needed. Its sometimes frustrating because running nautilus as root to navigate and delete/move/change permissions is often more convenient.
3. I'm fine running backups as each user, but it might be useful in the future to run it as root. I tried searching, but ran into some contradictions. What do you think?

Thanks for your help.

How can you "correct the ownership"?  Do you have a backup with the correct ownership somewhere?  **chown -R** probably is not sufficient and may cause more harm than good.

Running GUI tools - except Synaptic - as root is a poor practice.  You've learned part of the reason now, the hard way. 

I would NEVER run nautilus as root. No way.  I suspect you are ready to learn about file permissions - there are tutorials on the web and 30 minutes screwing around inside a terminal with **chmod** will teach more than you can imagine.  **Convenience is the enemy of security** ... except when it comes to ssh.  ssh is usually more convenient AND more secure than other alternatives. Go figure.

Backups ... odd you should mention that.  Check my signature for more resources. With a better understanding of file+directory permissions, you'll better understand why using root (or an equiv uid) for backups is absolutely critical.

I should point out that I do not use deja dup. I'm an **rdiff-backup** guy on a major level.  rdiff-backup can be as simple or as complex as you like.  If you have plenty of time and backup storage is about 20% larger than the source, something like:

```
sudo /usr/bin/rdiff-backup --exclude-special-files --exclude /Backups  / {userid}@{remote_srv}::/Backups
```
is all you need.  This command will take time the first run, but after that, only changed data will be "backed up".  I retain 30-60 days of backups for most of my systems.  Of course, that will get lots of things you don't need.  Being selective can easily reduce backup storage by all the OS files - just get the settings, personal and system, personal files, server data (DBs, website files, any other "system data") and a list of all the packages installed. Then you can restore using a nominal new box install and bring everything else back easily.

Don't forget to tell the backup area to remove older backup sets:
```
sudo /usr/bin/rdiff-backup --remove-older-than 60D  --force {userid}@{remote_srv}::/Backups
```
Simple.

It gets complex when you want to exclude certain types of files ... like music or videos ... things that don't change usually. I generally use pure rsync for those, but rdiff-backup for OS and personal settings and data files. Everything is automatic for those, but NOT automatic for large media files.

Clear as mud?

---

