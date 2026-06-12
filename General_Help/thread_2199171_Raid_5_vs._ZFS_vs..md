---
title: "Raid 5 vs. ZFS vs. ?"
date: 2014-01-12
forum: General Help
---

### Post by hwttdz on 2014-01-12
I'm midway through building a new computer.  Right now it only has a root drive in it, but I'm planning the media drives.  I'm planning on using 3 x 4 tb drives (I take a lot of photos), and would like to use raid 5, raid-z or something similar to get 8 tb usable space out of this set up.  Read/write speed is not a priority (those things will go to ram or the ssd), but data reliability is.  I'm worried about sudden reboots if I go with raid-z.  Should I be?  Is there something else I should be considering here?  I guess I'm also considering different filesystems.  I would lean towards ext4 mostly just because it's the default (assuming someone who knows more than I do made a reasonable decision).  Thanks.

---

### Post by TheFu on 2014-01-12
a) RAID-anything does not replace backups. PERIOD.  There are many failures for RAID that cannot be recovered from without backups.  For a home user, RAID is usually just a way to corrupt data on multiple disks concurrently.  Before dealing with RAID, get your backups AND recovery down perfectly.  Incremental backups mean having multiple copies of data that may have become corrupted over days, weeks, months.  Having just a mirror, is not really having a backup, IMHO. Versioned backups rock.

b) Current recommendations are for RAID6 or RAIDz2 due to issues around RAID5 and RAIDz where corrupted data _could_ be written to a disk during a difficult-to-cause power failures.  I've never experienced the "RAID5 hole" myself, but at the last HW update, switched from RAID5 to RAID10 here.

c) If you choose RAIDz or RAIDz2, then you will be using ZFS with all the fantastic-ness and terrible-ness that includes. This is not a decision to be made lightly. ZFS likes RAM.  8G is a minimal starting point for 4TB of storage.  With 8TB, you'll want 16G of RAM for the storage needs, more RAM is advanced stuff is used.

Also, you haven't stated if this is only a file server or both a file server AND desktop.  For a desktop, I would avoid RAIDz-every thing.

Ok, so now you have some ideas to research. Be careful to look for problems that people have with whatever level you decide. For example, look for clean upgrade paths for more storage.  As an example, ZFS wants 6 HDDs to start. It doesn't like 8. Recommendations are to build what you need now for the next few yrs.  I've always migrated my RAID storage using using backups - no attempt at "in-place" additions has been made. 
Every few weeks, someone posts that question on these forums. Definitely read the responses and proposed solutions.  For me, it is just always easier to keep a RAID set smaller than any single backup disk can hold - lots of reasons for this. Don't forget about format loss in those estimations for the backup locations.

FYI, I'm very cautious about storage.  Been using JFS the last 13 yrs and only switched to EXT4 about a yr ago for data. Had been using JFS, ext3 for boot partitions prior to that.  EXT4 wasn't proven enough to risk my data.  ZFS has been around a long-long time, but is mainly for 64-bit systems. The backport to 32-bit systems feels "scary" to me. Don't bother without a 64-bit OS and plenty of RAM.

Hopefully others will post different suggestions and experiences.

---

### Post by bab1 on 2014-01-13
> **hwttdz said:**
> I'm midway through building a new computer.  Right now it only has a root drive in it, but I'm planning the media drives.  I'm planning on using 3 x 4 tb drives (I take a lot of photos), and would like to use raid 5, raid-z or something similar to get 8 tb usable space out of this set up.  Read/write speed is not a priority (those things will go to ram or the ssd), but data reliability is.  I'm worried about sudden reboots if I go with raid-z.  Should I be?  Is there something else I should be considering here?  I guess I'm also considering different filesystems.  I would lean towards ext4 mostly just because it's the default (assuming someone who knows more than I do made a reasonable decision).  Thanks.

I'm going to take a completely different viewpoint from both you and @ TheFu.  As @ TheFu stated > RAID-anything does not replace backups. PERIOD. There are many failures for RAID that cannot be recovered from without backupsThe why of that statement is pretty interesting.  In the days of smallish HDD's RAID was a way to provide a layer of abstraction that allowed a larger partition over many physical drives.  Additionally , the ability to to replace a failed disk and rebuild the array quickly provided some measure of *hi-availability*.  RAID addressed large data stores over multiple disks and *hi-availability *only.  No thought was ever given to RAID being a backup solution.  With todays large disks and other disk aggregation methods there is really no need to employ RAID as an abstraction for creating a large.  In fact RAID is downright dangerous to rely on.

+1 on all the ZFS comments that @TheFu has stated.

The crux of the issue seems to be large disk aggregation and some sort of backup for data security.  I use LVM to create large partitions of multiple disks.  It's not as finicky as RAID or ZFS.  You can use different size and manufacture of disks to create volumes and you can add disks at any time.  In addition you can use all the disks for data rather than unneeded redundancy.  Any file system can be used on the LV.  I use Ext4 myself. 

I use Rsnapshot as the backup tool.  It's a set of PERL scripts that rely on rsync as the backup engine.  My backup store is a 8TB LV and my workstations are 2 TB LV.  I have never experienced a drive failure that cost me data.  I can restore the data within 30 minutes if need be.  I can recreate the LV in 15 minutes or so.

I say that if you have a typical small business (or home) network then you don't need the advantages of either RAID or ZFS.  It will be more efficient to use LVM and a simple robust backup system.  Even if you do decide to use RAID or ZFS you should use some backup routine for your data.

---

### Post by caymus on 2014-01-13
+1 bab1

For personnal home usage or SOHO, maybe it is better to take a look at:
 rsync + ext4 ahci storage on cheap sata racks ?
rsync is great.

I dont recommand zil/zfs for personnal / SOHO usage this is a payne, espacialy when zil is involved.
If you look for zfs, dont forget to take a closer look at zil

But i thing it is better to spend time & money around Rsync solutions.

---

### Post by TheFu on 2014-01-13
I love the advice from bab1 and caymus above.

I have lost data using LVM when extending across drives.  That happened when the 2nd drive, of 3, failed.  My knowledge of LVM was low at the time and all data on the other 2 drives was lost.  That event got me **Backup Religion**.

When it comes to backups, these are the things I look for in a solution:
[LIST=1]
[*]    Stable / Works Every Time
[*]    Automatic
[*]    Different Storage Media
[*]    Fast on the netwokr
[*]    Efficient with storage
[*]    Secure
[*]    Versioned
[*]    Offsite / Remote
[*]    Restore Tested
[/LIST]
[Reference]("http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups").

---

### Post by hwttdz on 2014-01-17
Ok, I'm sufficiently scared off of raid and zfs for the moment. I might try some sort of unioning filesystem in order to keep things in sync between the drives.  Thanks for the comments.

---

### Post by TheFu on 2014-01-17
If you need to keep things mirrored, **rsync** is THE TOOL. Make a tiny, script, and run it from the crontab periodically. Once a day or once a week.  More often than every 12 hours starts introducing the same issues that RAID1 has.  For large media, I use a weekly sync. That is enough that corrupt files can be found, but not over-written too quickly. Normal rsync is NOT good enough for backups of system settings or documents, IMHO. Versioned backups are important for that sort of data.

Not that you asked, but here's a trivial rsync script to mirror recorded TV shows between systems here:
```
#!/bin/bash
SRC="/Data/1.5T/T"
TARGET="hadar:/misc/usb_tv/T/"
rsync -avz --stats --progress --delete  $SRC/* "$TARGET"
```
It is destructive to the target location by design.

Another option is something called SnapRAID - it is like rsync, but uses parity. It seems to be designed for media. I've never used it and have trouble understanding how a 100% backup can be accomplished for 3 data drives with just 1 parity drive. I do not believe in magic.

---

### Post by bab1 on 2014-01-17
> **TheFu said:**
> If you need to keep things mirrored, **rsync** is THE TOOL. Make a tiny, script, and run it from the crontab periodically. Once a day or once a week.  More often than every 12 hours starts introducing the same issues that RAID1 has.  For large media, I use a weekly sync. That is enough that corrupt files can be found, but not over-written too quickly. Normal rsync is NOT good enough for backups of system settings or documents, IMHO. Versioned backups are important for that sort of data.

Not that you asked, but here's a trivial rsync script to mirror recorded TV shows between systems here:
```
#!/bin/bash
SRC="/Data/1.5T/T"
TARGET="hadar:/misc/usb_tv/T/"
rsync -avz --stats --progress --delete  $SRC/* "$TARGET"
```
It is destructive to the target location by design.

Another option is something called SnapRAID - it is like rsync, but uses parity. It seems to be designed for media. I've never used it and have trouble understanding how a 100% backup can be accomplished for 3 data drives with just 1 parity drive. I do not believe in magic.

There are a lot of clever folks out there. The rsync engine can be used to create incremental backups.  The basic idea comes from an [article]("http://www.mikerubel.org/computers/rsync_snapshots/") by Mike Rubel in 2004.  That idea was carried forward in [rsnapshot]("http://www.rsnapshot.org/").  Why create your own scripts when they are already available as a complete package?  I have daily, weekly, monthly and yearly backups using rsnapshot (rsync).

---

### Post by hwttdz on 2014-01-17
What are the issues you think that rsyncing every 12 hours would cause?  What do you mean that corrupt files could be found but not overwritten?

Explaining parity.  Imagine I have 3 drives, we'll call them A, B and P and for every bit b_i on P we will set it to:
P(b_i) = (A(b_i)  == B(b_i))
i.e. true if A and B have the same truth value (both true or both false, and false if they differ).
Then if drive X fails:
if X is P we don't care (since there was no 'data' there)
If drive A or B fails we can solve for what A or B contained using the same parity function, call Y the other working drive:
X(b_i) = (P(b_i)  == Y(b_i))
Note that no raid controller would actually implement this at the bit level, but the theory is more or less the same.  This can be extended over more drives by just counting the true bits over the drives at that location then doing a modulo 2.  So for N drives you can tolerate any one drive faulting.  This is the same theory behind raid 5 (of course parity is usually spread evenly over drives).

---

