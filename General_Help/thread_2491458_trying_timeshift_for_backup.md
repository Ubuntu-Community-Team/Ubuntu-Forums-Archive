---
title: "trying timeshift for backup"
date: 2023-10-09
forum: General Help
---

### Post by jgw on 2023-10-09
I decided to use timeshift to backup.  I installed it and ran it.  It asked me where to store the backup, etc.  No problems there.  Then it mada a snapshot.  I let it do its thing.  Then I took a look.  the snapshot that was created held nothing.  Then I started reading with more attention and learned that I was in trouble.  I think what happened is that timeshift decided to backup my entire system and, perhaps, just might do that.  I have no idea other than, sofar, nothing has happened.  I then googled something like: ubuntu 22.04 timeshift backup manual and found folders that said they were for installing and saying what to do.  I stopped there.

Apparently there is no manual and a lot of choices to find out what to do.  I assume that there are those who use timeshift and, hopefully, they will steer me to a place to study just what is going on.   As I said, I think its doing my entire system.  I have no idea, however, how to tell it what to backup or even if that is possible. 

Any thoughts would be appreciated.

---

### Post by mikodo on 2023-10-09
Hi,  

Have you looked at this page in GitHub:  

[https://github.com/linuxmint/timeshift](https://github.com/linuxmint/timeshift)  

It states that it is maintained at Linux Mint. Maybe more help is available there.

---

### Post by ajgreeny on 2023-10-10
Where did you ask timeshift to store the snapshot and are you using it as a backup for your personal files in home? There are better options for backing up /home than timeshift.

I've never used timeshift even when running Mint but if I remember correctly the default storage site is in the root filesystem which depending on partition setup could mean you run out of space for storage of snapshots.

If you use a separate /home partition that might be a better storage option but wait for others who know timeshift better than me before rushing to change things.

---

### Post by TheFu on 2023-10-10
Timeshift behaves different depending on which file system is used.
With BTRFS, it creates proper snapshots.  Those just freeze blocks of storage, but don't actually copy them anywhere, so if the drive fails, you don't actually have any backups. You can read more about this here: [https://osdn.net/projects/rebornos/wiki/Btrfs+system+snapshots+and+rollbacks+with+Timeshift](https://osdn.net/projects/rebornos/wiki/Btrfs+system+snapshots+and+rollbacks+with+Timeshift)

With every other file system, it uses rsync and will spend 2-20+ minutes copying everything over to a new location.  It is up to you do ensure that target location is a different drive with sufficient storage, not the same drive or partition.

I've heard that timeshift is designed to be used to backup the system, not user data.  That confuses me.  Why would someone want 2 different backup tools to accomplish 1 thing?  To each their own, I suppose.

To me, the confusing part of most backup tools is that they use the term "snapshot", which has a very, very, very, specific meaning in storage volume managers like BTRFS, LVM, and ZFS.  They "freeze" blocks making them immutable, but don't actually copy anything anywhere.  Creating a "snapshot" is step 1 in a backup process.  Then the newly created snapshot so mounted read-only and other tools are used to copy that frozen data safely somewhere else - to different storage.  This is actually a best practice for backups.  After the backup is made from the frozen blocks, it is ok to delete the snapshot, since we can't keep freezing blocks of storage on our primary disk forever. Eventually, there won't be any free blocks left to accept new or changed data.  Snapshots become a liability if left around using storage on the same physical storage device.

But if volume manager snapshots aren't used in the process, backup tools tend to call the resulting, last step, a snapshot. See my confusion?

So, you need to figure out which mode timeshift is working as your first step.

---

### Post by jgw on 2023-10-10
My system folders are in 2 4tb drives plus a 1tb ssd.  There are specific large folders I want to backup and wanted to use one of the drives to put the backups.  I was trying timeshift as that was the one suggested for ubuntu what was supposed to be the best one.  I used to use the backup that came with ubuntu but that one blew up on me and screwed everything up.

My suspicion is that using timeshift may not be the best way to go.  Too confusing.  I will, I guess, read a couple of other places claiming to have it all figured out but, so far, I am not delighted with timeshift. 

I also wonder about how much timeshift can backup.  For instance, if its a system backup can it backup my entire system onto one of the drives and still have enough room to store everything.  I have one 4tb drive which is approximately 2 thirds full.  The backup drive as 3.7tb open.  My main system exists on the 1tb ssd.  In otherwords, it might be possible to actually back up the entire kit and caboodle on the backup drive with no problem. Wonder if anybody has any thoughts on that one!

Thanks for the reply!

---

### Post by ne29914 on 2023-10-10
As a long-time Timeshift user, let me chime in.
Timeshift is excellent for system backups and has saved my behind so many times that I've lost count. It's stable and reliable.
I use it when experimenting or tweaking or installing something new or... you name it. Take a snapshot first and then proceed. If the experiment fails, Timeshift will bring you back to where you were.
I even tested it by issuing a "sudo rm /*" command to purposely crash my system/SSD. New installation and a Timeshift restore: back in business.

For document ( /home ) backups, I use BackInTime, because it's optimized for that job.

As @TheFu said, that might be odd, but it simply fits to my working style. Document backups I do every day, and I see no reason to include a system backup every time. Timeshift I use only before/after system changes.

---

### Post by #&amp;thj^% on 2023-10-10
Timeshift is designed on the premise you'll use something else for data. 
Options include rsync (in Terminal), Grsync, Back in Time and Lucky Backup. 
I use rsync. At times 3x daily, depending on what I'm doing at that session.
```
sent 32,823,201,293 bytes  received 14,582 bytes  88,353,205.59 bytes/sec
total size is 32,815,128,256  speedup is 1.00

```

---

### Post by jgw on 2023-10-12
Thanks for all the help!

I tried timeshift.  My problem is that I really don't want to backup my system.  All I want to backup is a couple very large folders.  I have a 4tb drive ready to handle the backups.  I tried to backup the two of the files to an empty drive with the backup that comes with ubuntu.  It promptly filled of a 4tb drive and then said it was broke (which didn't surprise, I used to use that one before it went nuts and blew up).  I also messed with timeshift.  I got as far as filtering the making the files I wanted to backup but never figured out how to get it to back them up even though there were supposed to backup as they were free to backup.  I could use rsync but what I would really want is an ap, or program, that will simply backup a folder then, anytime it changes the backup changes so they are always in sync.  Timeshift did, however, keep its backups pretty spare insofar as using space was concerned.  It would be nice if the backup I got also tried to limit the space used. 

I suspect such is out there and its hiding from me.....  

That's it.  I know, it sounds simple, but I guess not really?

---

### Post by #&amp;thj^% on 2023-10-12
This might help you then [https://ostechnix.com/grsync-a-simple-graphical-frontend-for-rsync/](https://ostechnix.com/grsync-a-simple-graphical-frontend-for-rsync/)
```
apt policy grsync
grsync:
  Installed: (none)
  Candidate: 1.3.0-1
  Version table:
     1.3.0-1 500
        500 http://archive.ubuntu.com/ubuntu mantic/universe amd64 Packages

```
Loosely termed a GUI for rsync.

---

### Post by TheFu on 2023-10-12
If you know part of the names for the files, you can search for them using either **locate** or **find** or **recoll**, but recoll is a bit of overkill for finding 2 misplaced files.  

**locate** will create an index daily. Files after the creation of the index won't be there until the next day. OTOH, it is google-fast. It only shows files that the userid running it can see. It doesn't look inside, just at the filenames.

**find** will traverse any storage you specify. This will take some time, but it is "live", meaning files added 1 second prior to running find will show up. It searches on file attributes, so name, size, owner, permissions, modified time, creation time ... stuff like that. It can also run other programs on the returned results.

**Recoll** is like having google for your own storage. It updates an index only when requested. Also, with some helper programs installed, it can look inside files like google looks inside webpages and PDF files, so searches aren't limited just to filenames like the other two options above.  After the index is updated, searches are extremely fast. Indexing can take some time.  

I use all three. Just depends on what I need to find and where I think the data is.  I try to use locate, since it is the lightest.

For backups, there are a few rules.  Always use a linux native file system, not NTFS. If you go out and buy a HDD, then connect it via USB and start copying files over, you are losing all the POSIX attributes. This might not matter for data files that are stored in a single user's HOME directory, but for proper backups of files that can have different owners, using NTFS is useless. You've been warned.  If you don't have any good reason to use NTFS, use ext4 instead on SSDs and HDDs.

---

### Post by MAFoElffen on 2023-10-13
+1 

When you buy a USB Backup Drive, they are normally pre-formatted as NTFS.  Just reformat it to something POSIX compliant, just like what you already have on your Ubuntu System. That is the easy way... 

I could go into many details on why NTFS is not a good choice. But that explanation is not really needed for what you want to do.

---

### Post by jgw on 2023-10-13
Thanks for the reply.  I have a 4tb drive connected by usb.  I do copy my files there.  The problem is that I have to do that.  I have one file that is a little less than 2tb long.  So, to copy it to the drive takes a very long time.  On top of that I have to have the old copy there until the new copy is done transferring.  

I should be able to find something that will copy the file and then update it if the original has changed.  As far as I can tell several will do that and shrink the backup file as well.  The problem with that is that they all seem to want to just work with the system itself and I don't want to do that.  rsync, I think, will do what I want and there is also a gui for that one.  I suspect that will be my next trial thing to see how that one works.  Does it, for instance, reduce the size of the backup data?  I have read several things on it but, so far, I suspect it doesn't reduce size but it may do that.  I just don't know.  

I have also learned that its possible to seriously speed up the usb connection  by getting a usb connection which increases the power to the target drive - using part of a sata connection (longer part) or a transformer plug.  I have tried a couple of those (usb outlets) but they don't seem to work and want microsoft and I don't use microsoft.  I am going to just keep on trying because I think I will find something that satisfies me.  There was a time when I would just write the program and have at it.  Those were the good old days. I also suspect that ai will, eventually, be available wherein one can give the ai parameters and the software will appear (I have faith <g>).

---

### Post by ne29914 on 2023-10-13
When you say drive, I suppose you mean a SSD.

Backing up a 2 TB file is a job, certainly. The backup systems I know of are file-based, meaning that if your 2 TB file changes, you'll have to create a second 2 TB file on your backup disk.
If you can, see if you can restructure this file into smaller parts that can be backed up separately. If possible, it will bring a lot of advantages, like increased speed (only the modified files will be backed up).

I've never used grsync, so no comment on that. For /home backup I use Back In Time, which is also rsync-based, but with a GUI optimized for data file storage.

Your "extra power USB speedup" is pure snake oil, but spend your money where you want.
The write speed of SSDs when storing large files is pure semiconductor physics, you can't change it.

---

### Post by TheFu on 2023-10-13
rsync doesn't do diffs when it is a local to local copy. It just copies the entire file again. Also, it doesn't compress the data on disk.  It can compress data streamed between systems.  You've never mentioned this.
Files that are already compressed on disk, shouldn't be compressed again. The extra CPU doesn't make up for the 1-2% additional compression.  If you are trying to copy a 2TB video file, there are better options.  If you are trying to backup a virtual machine file, there are better options.  If you are trying to backup a DBMS, there are better options.

The rsync manpage is clear on what it does, though it is long.
```
       You can also use rsync in local-only mode, where both the source and des&#8208;
       tination don&#8217;t have a &#8217;:&#8217; in the name. In this case it  behaves  like  an
       improved copy command.
```
This little trap is little known.  There might be a way to force it, but with really large files (anything over 15GB), it will be faster to just copy the file.  I know this from practical use.  My backups used to be based on rsync, but they were taking longer and longer. Soon, they didn't finish within the allocated backup window, so I had to figure out a different answer.  Now all those same backups take less than 1 hour total. Before they were over 8 hrs.  The change was pretty large and forced a complete re-think of my backups.

Canonical uses zsync to handle ISO image file re-re-re-distribution. Perhaps that will work better if you can only have 1 copy and only copy it locally.

If you can, split up the file into hundreds-thousands of parts, then back those up.  

What exactly is this single 2TB file?  There are probably better solutions.

If you don't use MS-Windows, then not using NTFS is even more important.

BTW, 1 copy isn't actually a backup. It is a copy.  Backups have multiple versions.

---

### Post by MAFoElffen on 2023-10-13
@jgw -- 

You never answered where the data is getting backed up to (asked 'again' by TheFu). And what this 2TB file is? That is very large for a single file. I am also curious about this.

TheFu is a wealth of knowledge on Backups. (Just search his userName.)

It would be good to know if the target media is local or remote to the source.

For remote, I tend to use scp and rsnc. I like that rsyync has a progress bar, can pause and resume. But scp is faster than rsync. 

If local, I usually use midnight commander, or rsync. If I am copying or moving pieces of data.. Yes, I seem to use rsync a lot. I know TheFu tends to use something else, which i keep forgetting what that is (sorry), and would like to learn more about that... Just because it seems to work good for him.

That is, if I'm not taking a snapshots of storage containers, which I usually do for backups. My present for that, for my ZFS systems is syncoid and sanoid.  I still use that manually, but it saves me about 5 to 10 commands. Still working on how I use that.

But TheFu and I are used to command line or console based screens, having control over things, and diving in deeply... I am old and have been around too long and sometimes feel old. We can tell you what we use, but what is really going to help "you" and you to be able to be good at for "now."

Previously, from time-to-time, I used [FreeFileSync]("https://freefilesync.org/"). I installed that on a lot of customer's Linux computers in the past. I know from your past threads, that you appreciated things that are simple, that doesn't have a big learning curve, and you can get good at with using it (in a hurry)... I think looking at that is worth your time. It has good documentation and tutorials to get you started.

---

### Post by jgw on 2023-10-14
Thanks for the replies!!

The 1.5tb file is a simple list of shows each show might have not only the episode video but a bunch of other stuff.  There are a LOT of these.  The drive I am backing up is a usb connection.  It takes, literally, to write the entire file to the backup drive.  This is why I am looking for something that will backup the file and then change it to match the original that changed.  I know there are a number of techniques that uses something like that rather than copying the file every time. 

Somebody suggested "Back in Time" might work.  I can also try that one. 

I should also add that I have another file that is just as big.  

The drive has an ext4 file system.  I wonder if I would save time and space if I simply zipped the file and sent that to the backup.  I could actually do that once a week which would actually backup enough for my needs.  I am not sure how much it would shrink as zipped but that just might work.  The other thing that would help is to juice up the usb port for the backup.  I keep trying them that claim they are selling that but, so far, doesn't work (they are cheap, for the most part)  I could also probably run a sata link from the computer to the backup drive which would solve the time problem (I think).

---

### Post by ne29914 on 2023-10-14
If by "show" you mean video clips/episodes, why are they all in one file? Makes no sense at all to me.

---

### Post by TheFu on 2023-10-14
> **ne29914 said:**
> If by "show" you mean video clips/episodes, why are they all in one file? Makes no sense at all to me.

+1!

Text files can be efficiently diff'ed, versioned and compressed.
Videos are pre-compressed, so doing more isn't useful, unless the codec used for the video really, really, really, sucks.  

I don't do versioned backups for audio or video files.  I do for nearly everything else.

---

### Post by TheFu on 2023-10-14
If you think the drive performance is the issue, it could be.  Run some tests. Gather actual facts.  Be certain to use the same units.  Either stick with MBps or Mbps.  You'll need to consider the entire hardware chain. The slowest part will make all the other parts limited to that performance.

[https://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results](https://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results) talks a bit about performance and tuning.

For most of us, SATA  or eSATA are the best connection options for our external storage.  There are others.  USB2 should be avoided.  Not all USB is the same. Most USB numbers are for "ideal situations", which never exist, so we can forget about the USB3 = 5Gbps and USB3.2 = 10Gbps stuff.  Those will never be achieved with real hardware.

---

### Post by jgw on 2023-10-15
First, the only ssd I use is the 1tb which I use for boot and general stuff.  All the rest of the 'drives' are really drives.  The ssd drives themselves are regular 4tb drives.  Regular drives, especially multi tb drives were less than regular drives at the time but ssd's are getting less.  Just saw an ssd, from China, for 46.95  (ssd's are coming down!).  

The shows are all in a folder.  The folder holds another folder for each show episode which includes the video as well as other information for that show and episode.  This is standard for the players (I use kodi)

Yep, I figure I will run a sata connection to the exterior for the backup.  If I can get a 4tb ssd for the right price I will just stick the backup inside the computer (no room for any more regular drives).  I would actually prefer using all ssd's.  Just waiting for the prices to go down.

---

### Post by ne29914 on 2023-10-15
> **jgw said:**
> 
The shows are all in a folder.  The folder holds another folder for each show episode which includes the video as well as other information for that show and episode.  This is standard for the players (I use kodi)

We're chasing a moving target here, and I'm slowly getting fed up.
First, it's a 2 TB file.
Now, it's a directory with subdirectories containing video files.

Well, what is it?

---

### Post by jgw on 2023-10-15
Folder/directory's range in size up to 1.2tb

I was unaware that what the folders was important - sorry....

The files are a directory with sub directories containing, amongst other things videos.

---

### Post by ajgreeny on 2023-10-15
The folder layout is not really of much consequence when backing up your home or just parts of it.
What matters is how much data is to be backed up and what size the destination is and how much of that is free for the backups to be saved into.
It also doesn't matter what files are in the source folder/filesystem; you are seem to be getting concerned about things that either I don't fully understand or I have missed something very important in this now long thread.
I am also beginning to think that you comment about a single 2TB file is possibly incorrect and that 2TB is the size of the total contents of a folder on your source disk. That, however, does not mean that you have a single 2TB file unless you have in some way concatanated all those episode video files into a single video file which I  suspect is not the situation.

Clarification needed please to overcome some of the confusion we are all feeling about this whole operation.

---

### Post by #&amp;thj^% on 2023-10-15
> **jgw said:**
> Folder/directory's range in size up to 1.2tb

I was unaware that what the folders was important - sorry....

The files are a directory with sub directories containing, amongst other things videos.

It's important always to know first hand what we are dealing with. (No guessing or you get guessing suggestions) 

By the way, I would ask myself whether I really have to move such a big amount of files at once. Batch processing is overrated. I try not to accumulate huge amounts of work if I can help it. (and I can)
And a small tip, If they reside on two different file-systems, use rsync:
```

rsync -av /source/directory/ /destination
```
To help understand this,  the trailing / on the source. This means it will copy the CONTENTS of the directory and not the directory itself. If you leave the / off, it will still copy the files but they will sit in a directory named /destination/directory. With the /, the files will just be in /destination

rsync will maintain file ownership if you run it as root or if the files are owned by you. It will also maintain the mtime of each individual file. (I'm not sure if you wanted/needed that)
This is My last post on this matter, and good luck no matter which method you choose.

---

### Post by jgw on 2023-10-21
Thank you all for the help.

I am going to set this as solved.  This backup thing is a lot more than I had expected and I am still trying stuff and there is a lot of stuff to try!

Thanks again!

---

