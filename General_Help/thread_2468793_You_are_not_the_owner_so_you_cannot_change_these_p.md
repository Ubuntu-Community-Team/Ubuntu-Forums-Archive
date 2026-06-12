---
title: "You are not the owner so you cannot change these permissions"
date: 2021-11-10
forum: General Help
---

### Post by tommy2k10 on 2021-11-10
My friend dropped tea on her laptop, hence there was no data seen on the disk.
She took it to a laptop repair company, who said the disk was burnt out and the data had been lost.
She has some very important stuff on there, so she asked me to have a  look, as I have used TestDisk before to recover data successfully.
Firstly, I tried Windows Explorer, to see if Windows could see it, with (as I thought) no success.
I then connected it to Ubuntu via my USB SATA caddy and it would  recognise the disk in Disk Utility but not in the 'Files' app under  Other Locations. In Disk Utility, the SMART data is fine, the disk is ok  with no bad sectors.
I then recovered some files successfully (I tested some by opening  them.) However, the disk is 1TB and the SSD in my laptop is only 256GB  so it filled up pretty quickly so I want to delete them from my SSD.
However, when I try to delete the files from the SSD it says 'You are now the owner so you cannot change these permissions.'
I have tried 'sudo chmod g+rwx /sdb/home/tom/documents/[name of file]' but that just says the file cannot be found. Do I need to put sdb2? 
Why isn't it letting me delete the files?

---

### Post by i-cat on 2021-11-10
sdb is usally an external device sda is your computers hdd

---

### Post by tommy2k10 on 2021-11-10
How that does make sense?! The drive mounts as sdb

---

### Post by TheFu on 2021-11-10
Blindly throwing commands at a computer without knowing which storage and which userids are involved is a great way to destroy not just the data, but your system.

A 2TB USB3 HDD is $45.  Have her buy one of those.  She clearly needs it so she can do backups.  Create and format at least 1 partition on it to receive the restored files.  Testdisk might find 50 versions of a file and you aren't able to figure out which is what or which is the most current version.  And you probably don't know the names.  1TB of files will be a huge amount of effort for someone to manually go though and search for that last version, rename, and copy back to the main storage location.  That's why I'd setup 1 partitions. One for the raw files and the other for the "good" files.

As for running chmod with sudo, you'll need to know what userid you are currently and what userid you want it to have and what permissions you want to lay down.  **chmod g+a** really isn't very useful in this situation.  Also, why would /sdb be used in the path? That doesn't make sense 99.9999% of the time.

Out of curiosity, do you not use tab-completion?  Bash and a number of other shells support it and you'll never get a filename wrong again. Ever.  Get on youtube to learn the technique. It is elegant and simple, but hard to explain.  I use it, perhaps 1,000/day out of habit. I remember having to be on systems with just Borne shell  which don't support "tab-completion".  It sucks.  Sometimes it is called "command completion" too.

---

### Post by i-cat on 2021-11-10
> **tommy2k10 said:**
> How that does make sense?! The drive mounts as sdb

Better open the disk utlity to see the mount path like in the attached image I posted.

on my hdd it is dev/sda dev/sda1 dev/sda2

p.s Yes I have the cat that chases my mouse icon . lolz

---

### Post by TheFu on 2021-11-10
> **tommy2k10 said:**
> How that does make sense?! The drive mounts as sdb

Doubtful.

Run the '**mount**' command to see where it is really mounted.  The device and the mount location seldom match.
Also, **df -Th** will show the mount device in column1 and the mount point/location in the last column.

---

### Post by The Cog on 2021-11-10
```
sudo chmod g+rwx /sdb/home/tom/documents/[name of file]
```is wrong on two levels.
Firstly, I think you probably mean /dev/sdb and not just /sdb.
Secondly, /dev/sdb is the device driver intarface to the raw disk contents. You do NOT want to write directly to this. The first thing you would overwrite would be the partition table. 

What you need to do is to mount the disk. You should see the disk show up in the left of the file manager or the disks utility, as i-cat posted. Mounting the disk (most likely a partition such as /dev/sdb1 rather than the raw disk /dev/sdb) makes the filesystem contents appear in the mount directory. That's where you could change permissions and copy files to/from if needed.

---

### Post by TheFu on 2021-11-10
Something else to consider.  If sdb1 is not a native Linux file system, probably NTFS or exFAT or FAT32, then permissions can only be controlled through mount options. chmod/chown don't work - ever.
**df -Th** will show the file system for mounted devices (partitions/slices/pools/LVs) too.

---

