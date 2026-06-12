---
title: "How can I implement a fast snapshot based incremental backup?"
date: 2013-05-04
forum: General Help
---

### Post by bubukind on 2013-05-04
Hey all,

I am currently researching methods for *quickly* backing up my home directory.

So far I have been using DejaDup and it kind of worked out for me when my laptop got stolen recently.
The problem that I see with DejaDup's and duplicity's file system-agnostic approach is that it cannot know which files change.
My home directory contains (among others) my photo collection which takes up around 300GB of space and since I keep adding tags and whatnot the files actually marginally change over time.
So with duplicity/dejadup a backup took long enough to keep me from doing regular backups since every picture had to be scanned.

I am at a point where I would be ok with "rolling my own" backup scripts to accomplish what I need but of course if anybody has pointers to projects that do what I want... :)

So maybe I should start with what I want from a backup:
[LIST]
[*]Reliable: I can actually restore the data 
[*]Secure: I keep my hard drive encrypted and I see no reason to have an unencrypted copy of it lying around 
[*]Consistent: On the off-chance that I perform major changes to my home directory while the backup runs I don't want to get an inconsistent view of it in the backup 
[*]Multiple plans: A plan for me consists of
[LIST]
[*]source (which folders to backup) 
[*]target (internal/external drive, ftp, rsync, ...) 
[*]schedule (daily, weekly, ...) 
[*]strategy for keeping/ditching old backups (e.g. keep the newest one, one from a week ago, one from a month ago and one from a year ago 
[/LIST]
  
[*]Fast: I do not want the backup to take longer than 5 minutes if i didn't change a lot. Of course, if I decide to reorder my photo collection, I must live with a long backup for the next increment. 
[/LIST]

So far I could find solutions that did everything except the "fast" part:
In particular, [bacula]("http://www.bacula.org") seems to be very powerful, even more than I actually need probably.
Rsync/Tar/Cron/pgp seems to be capable of doing everything I need, too.
I still really like duplicity, especially with the [Horcrux]("http://chrispoole.com/project/horcrux/") wrapper it seems to be pretty versatile.
But none of these tools seem to be making use of snapshot diffs [as btrfs offers them]("https://lwn.net/Articles/506244/")

I am running an LVM so I could use LVM snapshots but I cannot find a way of quickly determining the 'candidate list' of changed files.
In general, the use for snapshots in the backup process seems to be that they provide a consistent view of the file system while the backup runs, not so much for performance gain. 

Now the idea would be to use a file system that supports taking snapshots and comparing them to each other.
Then I would:

[LIST]
[*]Take an initial file system snapshot S1. 
[*]Every time I want to do an incremental backup:
[LIST]
[*]create a new snapshot S2 
[*]use some file system voodoo to get a list of changes or at least of the changed files between S1 and S2 
[*]use my backup script/application to only perform a backup of those files since no other files changed between the snapshots 
[*]reassign S2 to be the new 'current state', i.e. S1 <-- S2 
[/LIST]
     
[/LIST]

Does anybody know of tools to do that or something like that?
Or at least pointers to the commands I could use?
Which file systems support snapshot diffs? Currently I am running ext4.  Changing to btrfs would take a night of work (for my laptop, not for me  that is..) but would be possible.

Regarding duplicity, is there any way to pass in a candidate list of which files might have changed?
I see includes/excludes, but I am afraid that those have different semantics, i.e. the file list saved with the backup will change.
What I am looking for is mor like "assume all files to be unchanged except thos in the file I pass you as an argument."

Thanks all for your time. :)

---

### Post by Cheesemill on 2013-05-05
I use a combination of [LVM snapshots]("http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html") and [rsnapshot]("http://www.rsnapshot.org/").

My backup script does something like this....

[LIST]
[*]Create an LVM snapshot of /home.
[*]Mount the snapshot and use rsnapshot to create a backup from it.
[*]Destroy the snapshot of /home.
[/LIST]

This method ensures that the backup is in a consistent state as it is taken from a snapshot rather than a live filesystem, and rsnapshot handles backing up only the changed files as well as the backup retention policy.

---

### Post by bubukind on 2013-05-05
Hi Cheesemill :)

I had thought about using LVM snapshots already, but they don't give me the performance gain that I *could* get.
At least in my mind's eye or whatever... :P
The problem is that while an LVM snapshot is by definition in a consistent state, duplicity still has tu assume every file on the volume to be changed before it runs.
Thus it will scan every file on the volume and then only back up the ones that actually changed.

The btrfs send/receive mechanism seems to give you a very quick "diff" between **two** snapshots though.
So the idea would be to use that mechanism to narrow down the amount of files that duplicity (or rsnapshot) have to check *before* actually scanning the volume.

I think I might have to write some of this myself because the send/receive code was only introduced to btrfs last year so there might not be a "comprehensive" backup solution using it yet...

---

### Post by Cheesemill on 2013-05-05
I get your point, but at the end of the day does it really matter how long the backup process takes? As long as you are backing up from a snapshot instead of the running filesystem then you will have a consistent backup.

I'm currently looking into the more advanced features of btrfs myself, at the moment I'm only using it as a root partition for my 13.10 testing installation but I'll get back to you if I have any better ideas once I'm more familiar with the btrfs snapshot process.

---

### Post by bubukind on 2013-05-05
Consistency may be more important for a backup but personally I thing that speed is nearly as important.
The thing is that long backups bind my laptop (and thus me) to my desk, either for access to an external drive or for ethernet when doing off-site backups.
Thus, whenever DejaDup tells me that it would be time to back up my stuff I always think "do I have half an hour of time right now" instead of just hitting "go".
It is a bit like git vs svn when it comes to branching: when it is quick and painless you use it in a different, more useful way.

---

