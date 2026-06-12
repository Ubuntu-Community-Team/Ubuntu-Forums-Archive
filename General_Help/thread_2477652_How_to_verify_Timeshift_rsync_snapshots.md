---
title: "How to verify Timeshift rsync snapshots?"
date: 2022-08-02
forum: General Help
---

### Post by Advait on 2022-08-02
[SIZE=2][COLOR=#000000][FONT=Arial]Ubuntu 22.04 on an AMD laptop, ext4. Did a google search and didn&#8217;t find anything relevant. I&#8217;ve been using Timeshift rsync for a while. It seems to work good. Is there any tool that can verify my Timeshift snapshots? I want to make sure they&#8217;re not corrupted. [/FONT][/COLOR][/SIZE]

[COLOR=#000000][FONT=Arial]Does Timeshift verify snapshots after they&#8217;re created?[/FONT][/COLOR]

---

### Post by HermanAB on 2022-08-02
Rsync is a robust copy program and it verifies what it wrote. https://www.man7.org/linux/man-pages/man1/rsync.1.html

---

### Post by #&amp;thj^% on 2022-08-02
> **Advait said:**
> [SIZE=2][COLOR=#000000][FONT=Arial]Ubuntu 22.04 on an AMD laptop, ext4. Did a google search and didn’t find anything relevant. I’ve been using Timeshift rsync for a while. It seems to work good. Is there any tool that can verify my Timeshift snapshots? I want to make sure they’re not corrupted. [/FONT][/COLOR][/SIZE]

[COLOR=#000000][FONT=Arial]Does Timeshift verify snapshots after they’re created?[/FONT][/COLOR]

You'll know very quickly if it's not by way of output on restore:
Sample: "(process:13850): Json-CRITICAL **: 22:32:06.750: json_node_get_object: assertion 'JSON_NODE_IS_VALID (node)' failed
E: JSON data must be UTF-8 encoded"
I guess you could, *notice* I said "YOU" could ;) Creating checksum list at the source and copying it to the destination allows to monitor file corruption at all stages. (I'm not offering on this one :))
Example:
```

find . -type f -exec md5sum {} \; > list_01.md5
md5sum -c list_01.md5
md5sum -c list_01.md5 | grep -i failed
```
I'm not sure if this could or can't be done with Timeshift though.

---

### Post by TheFu on 2022-08-02
The only way that I know to validate a backup, is to perform a restore.  That has the added feature that the more we practice something, the better we are at performing it.

When I was switching backup methods from rsync to using a real backup tool with built-in versioning, since I wasn't backing up **everything**, just selected areas, it took 5 attempts before I had everything included in the backup to make for both the most efficient backup storage with the needed number of versions, not not too much more than was necessary.  Over the decades, I've added some helpful system information to my backups, since sometimes the problem isn't with just the files, but perhaps a partition table or driver or setting that was modified over time.  Perhaps I didn't reboot since making a change to some config file in /etc/ and the mistake only showed up at reboot time?  So, the last 10 backups would likely contain the same, wrong, settings, but 11 days ago, before I modified the file, that backup set has the correct settings.  Knowing that I can go back at least 90 day and often 180 days worth of backups for very little extra storage or backup time, lets me sleep much better at night.

Test your backups via a restore. That's the only way to be certain.

---

### Post by tea for one on 2022-08-03
> **TheFu said:**
> Test your backups via a restore. That's the only way to be certain.
Yes, that is the only way to be 100% sure,

However, just for information, have a look at [https://clonezilla.org/](https://clonezilla.org/).
After creating an image of your disk/partitions, there is a menu option:-
[COLOR="#0000FF"]chk-image-restorable[/COLOR]
Possibly useful for your peace of mind?

When you first create an image with Clonezilla, there is also the option to double-check that the image is restorable.

---

### Post by TheFu on 2022-08-03
Lots of backup tools validate the target and source files match, usually with some sort of checksum. A few use cryptographic signatures.

Cloning tools and backup tools are different. They each have a purpose.  Best not to confuse them.

---

### Post by Advait on 2022-08-05
> **TheFu said:**
> The only way that I know to validate a backup, is to perform a restore.  That has the added feature that the more we practice something, the better we are at performing it.

When I was switching backup methods from rsync to using a real backup tool with built-in versioning, since I wasn't backing up **everything**, just selected areas, it took 5 attempts before I had everything included in the backup to make for both the most efficient backup storage with the needed number of versions, not not too much more than was necessary.  Over the decades, I've added some helpful system information to my backups, since sometimes the problem isn't with just the files, but perhaps a partition table or driver or setting that was modified over time.  Perhaps I didn't reboot since making a change to some config file in /etc/ and the mistake only showed up at reboot time?  So, the last 10 backups would likely contain the same, wrong, settings, but 11 days ago, before I modified the file, that backup set has the correct settings.  Knowing that I can go back at least 90 day and often 180 days worth of backups for very little extra storage or backup time, lets me sleep much better at night.

Test your backups via a restore. That's the only way to be certain.

Seems that practicing restore on my live system is risky. I can set up an Ubuntu VM and play around with Timeshift restore there. That will help me learn.

---

### Post by Advait on 2022-08-05
> **tea for one said:**
> Yes, that is the only way to be 100% sure,

However, just for information, have a look at [https://clonezilla.org/](https://clonezilla.org/).
After creating an image of your disk/partitions, there is a menu option:-
[COLOR=#0000FF]chk-image-restorable[/COLOR]
Possibly useful for your peace of mind?

When you first create an image with Clonezilla, there is also the option to double-check that the image is restorable.

I make a daily Clonezilla full clone of my main drive. I never make images cuz if my main drive fails I can just yank out the failed drive and install the clone and be back up and running easily. 

I found a screenshot of where Clonezilla asks if you want to verify restoreability of an image before restoring. I haven't yet found a way to verify a clone. Is there a way to verify a clone?

---

### Post by Advait on 2022-08-05
> **TheFu said:**
> Lots of backup tools validate the target and source files match, usually with some sort of checksum. A few use cryptographic signatures.

Cloning tools and backup tools are different. They each have a purpose.  Best not to confuse them.

Yep. I make daily Clonezilla clones so if my main drive fails I can yank it out and install the clone and be easily up and running again.

And I use Free File Sync to make daily backups of all my user data files to multiple external drives.

Would it be helpful for me to also make images?

---

### Post by TheFu on 2022-08-05
There are lots of opinions about how to make backups.  I think images are the wrong answer.  Hard to have 180 days of images to combat malware that was sitting on the system the last 90 days, unused.  This is a common tact now. Delay letting the admins/owners know they've been infected beyond what their backups hold.

Nobody except govt have enough storage for more than a few image-based backups.
Whereas everyone can easily support 180+ days of backups with file-based versioning and selective backups.  There's a trade-off, of course.  The ease of the restore vs the flexibility vs the time to restore.  Everyone needs to figure out the right mix of those for themselves.  I know that it takes about 45 minutes to fully restore any of my systems from the time I decide it is necessary.  Some are more like 15 minutes, but most are closer to 30 minutes.  I know this from lots of testing and actually restoring the systems for a number of different reasons, not all are dumb-admin mistakes, but some are.  Most of the time, I need to restore just a few files.

Also, image-based backups almost always requires downtime to create and at least 45 minutes (often 90 min) to create, so those just aren't options.  
Here are some backup times from last night for a few of my systems:
```

=== Time for Backups to pihole === 
StartTime 1659675663.00 (Fri Aug  5 01:01:03 2022)
EndTime 1659675678.85 (Fri Aug  5 01:01:18 2022)
ElapsedTime 15.85 (15.85 seconds)
TotalDestinationSizeChange 1463100 (1.40 MB)


=== Time for Backups to spam1 === 
StartTime 1659675683.00 (Fri Aug  5 01:01:23 2022)
EndTime 1659675683.66 (Fri Aug  5 01:01:23 2022)
ElapsedTime 0.66 (0.66 seconds)
TotalDestinationSizeChange 1071 (1.05 KB)


=== Time for Backups to wallabag === 
StartTime 1659675687.00 (Fri Aug  5 01:01:27 2022)
EndTime 1659675692.54 (Fri Aug  5 01:01:32 2022)
ElapsedTime 5.54 (5.54 seconds)
TotalDestinationSizeChange 49397 (48.2 KB)


=== Time for Backups to vpn === 
StartTime 1659675699.00 (Fri Aug  5 01:01:39 2022)
EndTime 1659675699.90 (Fri Aug  5 01:01:39 2022)
ElapsedTime 0.90 (0.90 seconds)
TotalDestinationSizeChange 953 (953 bytes)


=== Time for Backups to hadar === 
StartTime 1659675705.00 (Fri Aug  5 01:01:45 2022)
EndTime 1659675742.44 (Fri Aug  5 01:02:22 2022)
ElapsedTime 37.44 (37.44 seconds)
TotalDestinationSizeChange 188675138 (180 MB)

```
You decide.  Is that fast enough?  Those are "pulled" backups. The backup server remotes into each client and "pulls" the needed data to restore.   I've posted in these forums a number of times how much storage is used for each version and the totals.  I didn't show some other systems which have hundreds of thousands of files that take a bit longer, but all are less than 25 minutes each to backup.  Screw it, here's the worse:

```
=== Time for Backups to zcs45 === 
StartTime 1659682896.00 (Fri Aug  5 03:01:36 2022)
EndTime 1659684165.40 (Fri Aug  5 03:22:45 2022)
ElapsedTime 1269.40 (21 minutes 9.40 seconds)
TotalDestinationSizeChange 210695908 (201 MB)
```

YMMV, but 60 days of daily backups usually needs about 1.2x the source storage. I'm selective about what is included. I've posted about those multiple times in these forums too.  Just depends on how much changes over time and if any huge files are accidentally backed up.  I keep huge files on NFS storage and don't do versioned backups for those files, just an easy mirror. This is due to the storage required.  Documents, settings, are all backed up daily, along with a list of manually installed packages so I can effectively get the system back with very little real hassle.

rsync mirroring gets about 80% of what an ideal backup would need.  The lack of versioned file metadata is a huge concern.  Lots of backup tools have this same problem. They get the data and the most recent owner, group, permissions, ACLs, and xattrs, but not the why those things change over time.  I hope that timeshift does something so save those things.  Backup tools that are based on rsync+hardlinks do not.  rsnapshot, back-in-time, and similar tools included.  rdiff-backup and duplicity **do** capture file metadata changes over time.

---

### Post by Advait on 2022-08-05
> **TheFu said:**
> Whereas everyone can easily support 180+ days of backups with file-based versioning

Does btrfs provide 'file-based versioning'? Is 'file-based versioning' part of the magic of COW file systems?

Is 'file-based versioning' not possible with ext4?

---

### Post by TheFu on 2022-08-06
Any file system can "support" versioned backups, just like marketing people can (in my country) claim that Vitamins "support" fighting X disease or Y virus or Z healthing lifestyle.
A file systems doesn't move data from A --> B for the purposes of backups.  We have to do that with separate commands.  Some make it easier. It is harder to accomplish than my words make it sound.

[https://fedoramagazine.org/btrfs-snapshots-backup-incremental/](https://fedoramagazine.org/btrfs-snapshots-backup-incremental/) tries to explain using btrfs for remote snapshot sending. It seems similar to ZFS with a btrfs send command.  BTRFS snapshots on the same physical device are never backups.  ZFS has the zsend command for a similar result - transmitting snapshots to remote backup storage on another computers.

What btrfs DOES allow, which is the same as what LVM and ZFS allow, is the creation of true volume management snapshots.  A snapshot is nearly instantaneous and freezed specific blocks until the snapshot is removed.  Those blocks cannot be altered (logically) when contained inside any single or multiple snapshot.  Until the named snapshot is used to move the bytes to new storage hardware, there isn't any backup.  But when a snapshot is used to freeze the blocks, we can be as close to 100% certain as possible that the files will not change during the byte copy process to other storage.  For files that are actively being used, say a DBMS data file or index files, having these frozen blocks is absolutely critical to get clean, valid, backups.  Backing up open() files being written is a good way for corrupted backups of those files.

Don't confuse "snapshots" as used by nearly all backup tools as being the same as the volume management snapshots.  This is criminal, IMHO.  It leaves people thinking the wrong things.  The similar thing that has been perpetrated on computer users worldwide is the idea that a partition is a drive that MSFT did.  There is not D: drive.  It is a D: partition.  We come across this all the time here with people being confused between a partition and a drive, sometimes leading to data corruption or data loss or just bad backups, because they've been lied to by MSFT since the first HDDs were available.  Misunderstanding of what a "snapshot" is, can lead to the same issues.  Please learn the difference.

Real snapshots have uses beyond being used for data backups.  By understanding what they can and cannot do, you won't have the wrong expectations and hopefully, won't have massive data loss due to that misunderstanding.

Anyone using btrfs really needs to read and re-read this article until they understand the limitations: [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)  It isn't all rosy.  For a single-disk system, say a laptop, brtfs is probably a great file system, provided no virtualization is being used.  There are a few of caveats like that with BTRFS.  Virtual machines don't like the CoW BTRFS implementation and data corruption is a common problem.  There are ways to disable the problem settings for the storage areas where VMs storage is placed.  Will anyone really do that who isn't a professional admin?  Doubtful.

Timeshift shouldn't use rsync for backups on btrfs. Rsync is a fall-back mode when btrfs isn't available.  

That's all I know. Hopefully, it isn't too confusing.

---

### Post by Advait on 2022-08-06
#TheFu. Thanks for the details about btrfs and snapshots. I'll have to re-read it a few times to properly understand. When I get some free time, I plan hire an online tech support person to help me wipe out and re-create my system with Ubuntu on top of btrfs. 

Also thanks for the heads up re btrfs and VMs. Good tip.

---

### Post by TheFu on 2022-08-06
> **Advait said:**
> #TheFu. Thanks for the details about btrfs and snapshots. I'll have to re-read it a few times to properly understand. When I get some free time, I plan hire an online tech support person to help me wipe out and re-create my system with Ubuntu on top of btrfs. 

Also thanks for the heads up re btrfs and VMs. Good tip.

Nobody cares for your data like you do.  I think that hiring someone for a long-term engagement can make sense, but expect to spend $1000/yr, otherwise it won't be worth their time to think long term.   I've tried to think long term for all my clients, but they seldom need to get help later and they certainly don't like the costs.

There isn't much that an online tech support can actually do to install an OS on consumer hardware.  Do you have a server with IPMI?  Without that, do you really expect that person to come to your location to do the install?  Without that, I don't see this being all that useful.  But if you have a relative who is a Linux nerd, you might trade a holiday visit for computer work. ;)

---

### Post by Advait on 2022-08-07
> **TheFu said:**
> hiring someone for a long-term engagement can make sense, but expect to spend $1000/yr, otherwise it won't be worth their time to think long term.

It will be a short one-time job, maybe 2-3 hrs max. They'll be on the phone to guide me as I setup btrfs and then install Ubuntu; and then they'll give me a quick training in how to make btrfs snapshots best practices. (As soon as Ubuntu is up and running they'll be able to remote connect.) Should be pretty easy for a good Linux admin. I'm good at following directions from a skilled tech person. I've already used remote support a few times and it's all gone well.

And I'll do multiple backups and clones before starting.

---

### Post by TheFu on 2022-08-07
> **Advait said:**
> It will be a short one-time job, maybe 2-3 hrs max. They'll be on the phone to guide me as I setup btrfs and then install Ubuntu; and then they'll give me a quick training in how to make btrfs snapshots best practices. (As soon as Ubuntu is up and running they'll be able to remote connect.) Should be pretty easy for a good Linux admin. I'm good at following directions from a skilled tech person. I've already used remote support a few times and it's all gone well.

And I'll do multiple backups and clones before starting.

Most of that is available by membership with a LUG.  Just need to find the right one that meets when you can attend and has experts who are knowledgeable on the subject you'd like to learn.  

My LUG meets weekly and does a fresh install for all to see a few times a month, but the installs typically are not Ubuntu-based.  Last week, we did 2 - the latest Lubuntu with LVM+ext4 (I wanted to test some virt-manager stuff)  and the just released Linux Mint with ZFS (which turned out badly with terrible performance and Timeshift defaulted to using rsync backups). They reinstalled Mint using BTRFS because the goal was to show how to use timeshift with snapshot-based backups.  I wasn't really watching too closely.  I am tempted to gain a little direct btrfs experience by loading it onto a laptop, but I need LUKS encryption on my portable devices and I don't know if that is supported through the installer. I've seen 20-step guides for setting up LUKS and BTRFS, that's just a bit more than I'm interested in doing for an install.  

We all have slightly different needs and limits, I suppose.

---

### Post by Advait on 2022-08-07
> **TheFu said:**
> Most of that is available by membership with a LUG.  Just need to find the right one that meets when you can attend and has experts who are knowledgeable on the subject you'd like to learn.  

My LUG meets weekly and does a fresh install for all to see a few times a month, but the installs typically are not Ubuntu-based.  Last week, we did 2 - the latest Lubuntu with LVM+ext4 (I wanted to test some virt-manager stuff)  and the just released Linux Mint with ZFS (which turned out badly with terrible performance and Timeshift defaulted to using rsync backups). They reinstalled Mint using BTRFS because the goal was to show how to use timeshift with snapshot-based backups.  I wasn't really watching too closely.  I am tempted to gain a little direct btrfs experience by loading it onto a laptop, but I need LUKS encryption on my portable devices and I don't know if that is supported through the installer. I've seen 20-step guides for setting up LUKS and BTRFS, that's just a bit more than I'm interested in doing for an install.  

We all have slightly different needs and limits, I suppose.

Unfortunately I live in a rural area with no LUGS nearby. I did a search and found a page that shows how to install btrfs when installing Ubuntu. Looks pretty easy. Maybe I can do it myself! O:)

---

### Post by TheFu on 2022-08-07
> **Advait said:**
> Unfortunately I live in a rural area with no LUGS nearby. I did a search and found a page that shows how to install btrfs when installing Ubuntu. Looks pretty easy. Maybe I can do it myself! O:)

COVID pushed LUGs online.  If you can do a video meeting, you can attend any LUG that is convenient for time and language, though I suppose you can get up in the middle of the night and listen to people using a language you don't speak too. ;)

---

### Post by Advait on 2022-08-09
> **TheFu said:**
> COVID pushed LUGs online.  If you can do a video meeting, you can attend any LUG that is convenient for time and language, though I suppose you can get up in the middle of the night and listen to people using a language you don't speak too. ;)

:) I'll practice my lucid dreaming and attend a LUG in my OOBE form. Although it would be hard to work the mouse... ;)

This forum, the reddit linux subs and other linux forums are decent substitutes for a real LUG. The helpful Linux communities have been key for me sticking with Linux when I was having lots of issues. Now I'm a lot more comfortable with it.

---

### Post by TheFu on 2022-08-09
> **Advait said:**
> :) I'll practice my lucid dreaming and attend a LUG in my OOBE form. Although it would be hard to work the mouse... ;)

Last week, my LUG had attendees mostly from the Eastern US, but also Singapore and Denmark.  Of course, not every meeting is great for everyone who attends.  We discuss the "why" for many things, but also try to show examples. The key for any attendee is to introduce themselves or we'll consider that person a troll and kick them out.  We really want to be welcoming to everyone, but it is a 2-way street to access the many experts attending.

It is sad, but we've had a group of trolls attempt to take over the meetings a few times, so the core members were forced to take anti-troll mitigations which makes joining just a bit harder and we have a much shorter "kick-out" period for non-responsive new people. After attending and participating in a few meetings, we relax a bit.  New people need to have a microphone working or be quick to answer in the chat.

---

### Post by Advait on 2022-08-12
> **HermanAB said:**
> Rsync is a robust copy program and it verifies what it wrote. [https://www.man7.org/linux/man-pages/man1/rsync.1.html](https://www.man7.org/linux/man-pages/man1/rsync.1.html)

See text below from the rsync man page. It seems this is the smoking gun for rsync verification. True?
----------
Note that rsync always verifies that each *transferred* file
              was correctly reconstructed on the receiving side by
              checking a whole-file checksum that is generated as the
              file is transferred, but that automatic after-the-transfer
              verification has nothing to do with this option's before-
              the-transfer "Does this file need to be updated?" check.
-------------

---

### Post by Advait on 2022-08-12
> **TheFu said:**
> It is sad, but we've had a group of trolls attempt to take over the meetings a few times, so the core members were forced to take anti-troll mitigations which makes joining just a bit harder

If I join I promise to be a llort (the opposite of a troll). :P

---

