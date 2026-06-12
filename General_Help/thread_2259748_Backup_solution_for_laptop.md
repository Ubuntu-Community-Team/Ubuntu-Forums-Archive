---
title: "Backup solution for laptop"
date: 2015-01-06
forum: General Help
---

### Post by Andy_Lawson on 2015-01-06
Hi,

I'm looking for some suggestions for backup solutions.

I primarily want to backup the system state on my personal laptop (running Ubuntu 14.04), initially to a local destination.
I have a small SSD (32G) that holds the root partition and a large spinning disk (500G) that holds /home

I'd like the backup to run automatically, every day or so, and backup the whole of the SSD to the disk (preferably, transparently while the OS is up and running) such that I can restore the entire system with some bootable media and the files from the disk.

Later, I'd be looking to use the same or a similar system on a number of Ubuntu desktops I have dotted around.
It'd also be great if the backups were flat files that could be pushed up to Crashplan or similar.

Does anybody have any recommendations in this space?
It may be that what I want is not possible, but I just wanted to ask and check :)

Thanks!
Andy.

---

### Post by TheFu on 2015-01-06
duplicity, rdiff-backup, tar, rsync+hardlinks, back-in-time ... there are many possible solutions if you don't care so much about wasted storage for the versioning.  UNIX/Linux have solved this for decades.

duplicity has many GUI options - duplicati, dejaDup, and probably a few others.  This set of tools, supports encryption, which is mandatory for remote locations.

Of course, if you run a DBMS, then you'll need to take steps to quiesce the DB data before the backup.  That can apply to other applications too. Just depends on what you run on the system.

---

### Post by Andy_Lawson on 2015-01-06
I had a look at back-in-time, thanks for that.

All the tools you mention seem to be file-level backup tools. I was really looking for something to backup the disk partitions as a whole.
Do you know of anything available in that arena?

---

### Post by Mark Phelps on 2015-01-07
There is Clonezilla -- which I use regularly to do image backups, but it fails to meet (at least) two of your requirements:
1) It can't be use to backup a partition that is being used. You have to boot from CD/USB or Clonezilla.
2) It doesn't create "flat" files -- they are compressed images.

---

### Post by Andy_Lawson on 2015-01-07
Thanks Mark - I've used Clonezilla a few times.
I guess I was trying to avoid putting it like this, but I think I'm really looking for Linux version of ShadowProtect.....

---

### Post by TheFu on 2015-01-07
if you run LVM or ZFS, you can use snapshots. That is more complex than you probably want and can waste lots of storage.

Clonezilla, partimage, fsarchive  can be used to image partitions - but not while active.  Ok - well, I suppose you could use them when active, but don't expect the image to be useful later, it won't be "consistent."  Plus it will be a full-backup every time.  The first set of tools mentioned are in a group that does incremental backups - so just a few minutes per system is needed after the initial backup happens.  Highly convenient.

---

