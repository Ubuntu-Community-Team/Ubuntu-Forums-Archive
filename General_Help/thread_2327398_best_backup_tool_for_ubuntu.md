---
title: "best backup tool for ubuntu"
date: 2016-06-10
forum: General Help
---

### Post by kaky951357 on 2016-06-10
hello,
i have a few problems whith my laptop, every time i use a terminal i kill my system :D ,and it so boring to reinstall ubuntu and lost all or some of my data, the last time i used deja-dup it not saving application and all personnalisation that i add to my system ,so i came to you to propose me a solution to completely save my data and personnalisation on a partition that i will create on my HDD or a external drive and if possible a simple to use tool :)
thank you for help

---

### Post by X-RED_Tech on 2016-06-10
Deja-dup does not save installed apps but it does save everything at /home and that includes all your personal settings.

---

### Post by kaky951357 on 2016-06-10
after i restore my backup i don't found my exacte préférences (wallpaper, custom graphical effects ect)

---

### Post by oklokl on 2016-06-10
[http://www.clonezilla.org/](http://www.clonezilla.org/)
[http://www.sysresccd.org/](http://www.sysresccd.org/)
[http://www.acronis.com/en-us/personal/computer-backup/](http://www.acronis.com/en-us/personal/computer-backup/)
^^

or sync..

---

### Post by Habitual on 2016-06-10
> **kaky951357 said:**
>  came to you to propose me a solution to completely save my data and personnalisation on a partition that i will create on my HDD or a external drive and if possible a simple to use tool.
thank you for help

I suggest you create a partition in ext4 and mount it at /home.
Someone here I hope, can guide you through it.
This separate partition can save you hours and hours of needlessly restoring from backups.
I've had the same /home for 8 years. Never lost a thing.
We can then Install an OS a day, wouldn't matter.

---

### Post by alain.roger on 2016-06-10
I would like to know why every time someone says rsync as backuping tool. it is a synchronization tool so no backup in fact, just a mirroring of files. If source is damage because synchronization, targeted sync directory will also be corrupted. a backup at  T time is normally not corrupted. Moreover rsync do not compress to save disk space AFAIK.

I'm looking for also a good backup tool. I used for months Areca but since 08.2015 there is no update...in fact the only backup tool with update is bacula.org but it is a network system :(

---

### Post by DuckHook on 2016-06-10
> **alain.roger said:**
> I would like to know why every time someone says rsync as backuping tool. it is a synchronization tool so no backup in fact, just a mirroring of files.Actually rsync is endlessly versatile and can be used for backing up as well as synchronizing. In fact, a backup is nothing more than a one-time synchronization with the resulting media taken off line and stored someplace safe.> If source is damage because synchronization, targeted sync directory will also be corrupted. a backup at  T time is normally not corrupted.This does not make sense. If the source is corrupt at any moment in time, then an image taken of that source will also be corrupt, irrespective of whether one calls it a "synchronization" or a "backup" The old adage: "Garbage in, garbage out" applies to data more than to just about anything else.> Moreover rsync do not compress to save disk space AFAIK.*rsync* easily compresses data with the -z switch. You may wish to learn more about *rsync* before dismissing it so casually. In fact, *rsync* is one of the most powerful and versatile tools in the Linux toolbox and is used as the basis for all sorts backup front-ends. Deja Dupe is merely a pretty graphical overlay on top of rsync.> I'm looking for also a good backup tool. I used for months Areca but since 08.2015 there is no update...in fact the only backup tool with update is bacula.org but it is a network system :(Unless you are an enterprise-level network of multiple servers, for most regular users, the aforementioned Deja Dupe is all that is necessary for good backups. It is simple to use and already bundled with all 'buntu flavour installs. The app is referred to simply as "Backup", but technically, its proper name is Deja Dupe.

For backups, *rsync* can be used in the raw without the pretty front ends. However, if anything, it is so powerful that it suffers from complexity and can be overwhelming for new users:```
man rsync
```An easy guide to using Deja Dupe appears in my signature.

---

### Post by DuckHook on 2016-06-10
**Addendum**

It is often easier for newcomers to overcome *rsync*'s intimidating complexity with a graphical shell called *grsync*:```
sudo apt install grsync
```This shell will limit your options to only those most often-used, but this is usually enough for most real-world cases. For real power though, there is nothing like the rsync command line. The following Wiki page might prove useful: [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by HermanAB on 2016-06-11
Most (all?) backup tools are simply a GUI wrapper over rsync, which ultimately makes rsync less powerful and more difficult to use...

---

### Post by kevdog on 2016-06-11
Without going into rants about the abilities of rsync, I would answer the OP's question asking him his requirements for a backup.  There are many backup tools available, however many differ in their features, and no backup solution is perfect.  Because I can't speculate what the poster's needs are, I'll just give some examples.  I have a local backup solution in place that shares data between many computers and a server, all located in my home.  This is a local backup.  All computers are backed up using rsync.  For redundancy, the local server (ubuntu), also runs a afp server which the computers that run OSX can take advantage of via the Time Machine utility.  I believe Time Machine and rsnapshot to be very very similar.  For those wondering, I configured the AFP server according to this guide: [https://www.outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/](https://www.outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/). 

Paranoid over backups due to a lightening storm that seemingly knocked off a lot of my computers and my backup server located in my house during a very bad storm, I was seeking another solution. I also wanted an offsite backup away from the local backup.  There are probably many ways to accomplish this, but in this scenario I really wanted to due an encrypted backup solution, since I knew I physically wouldn't have total control at all times of the offsite backup server.  Additionally, since the backup was offsite and I wanted to be as stingy about bandwidth as possible, I wanted a backup solution that would only transfer diffs of changes and not very large files where only a portion of the files may have changed (think of a virtual disk image).  I also wanted the solution to possibly be as universal as possible with the ability for different types of computers (Windows, Mac, Linux) to have the ability to take advantage of the backup solution. After searching through an exhaustive list, I'm currently evaluating both obnam and borg as programs for backup given this criteria.  Both allow for encryption, transfer diffs, and keep snapshots of prior backups similar to rsnapshot.  Borg requires borg to be installed on the server if you would like to do fast backups, whereas obnam does not. Obnam however requires either linux or OSX and may possibly run through cygwin in windows -- I haven't evaluated this thus yet.  Both programs are very slow however. Both allow the user to mount the remote repository using FUSE, which can at times be buggy.  I can see these two programs not being ideal for everyone, however they seem for right now to fulfill my requirements for my offsite backup.  rsync is just dang easy and fast to use and very easy to use over ssh.

---

### Post by CharlesA on 2016-06-11
How are you liking borg so far? I'm currently playing around with it and thinking of migrating it it from rdiff-backup mostly for the encryption, checksumming and deduplciation. Not sure if it is a good fit or not, though.

---

### Post by kevdog on 2016-06-11
My experience with borg --- ehh.  I've been testing it for the last month.  Features I like.  Really compresses the heck out of the backup.  For example -- All archives together are 3.48 Tb however the compressed deduplicated size is 284 Gb.  I find that to be astonishing. Fairly simple to set up, however I hate how you have to pass the encrypted password to the program --- however I'm not sure how else you would do it if you're utilizing a cron job for example with borg.  The actual backup process for the initial archive was very slow, and it seems the nightly backup process is also really slow.  I'm running borg on the remote server as well -- I'd hate to see the performance without borg running on the server.   My only other basis of comparison is obnam, which to tell you the truth -- after all I've read, daily backups are actually a lot faster -- maybe 3-4x as fast.  The initial backup however was really slow. I don't however know how much compression of deduplication I'm getting from obnam.  Obnam is a little bit more Debian focused --- in fact it's only developed for Debian, so running it in not debian type distro's is kind of tricky, although it can definitely be done.  I'm still in process of comparing the two, and of course I've got to do a big wipe out of my original files and restore from the backup archive.  I haven't done this yet -- a backup isn't a backup until you've had to do a restore IMO.  I'd be interested in hearing you're experience.

---

### Post by RobGoss on 2016-06-11
You can also use **Clonezilla** but this method clones the entire system but yet very reliable

---

### Post by RobGoss on 2016-06-11
What version of Ubuntu are you using it maybe a good idea to switch to another and see if it continues to crash.

---

### Post by CharlesA on 2016-06-11
> **kevdog said:**
> My experience with borg --- ehh.  I've been testing it for the last month.  Features I like.  Really compresses the heck out of the backup.  For example -- All archives together are 3.48 Tb however the compressed deduplicated size is 284 Gb.  I find that to be astonishing. Fairly simple to set up, however I hate how you have to pass the encrypted password to the program --- however I'm not sure how else you would do it if you're utilizing a cron job for example with borg.  The actual backup process for the initial archive was very slow, and it seems the nightly backup process is also really slow.  I'm running borg on the remote server as well -- I'd hate to see the performance without borg running on the server.   My only other basis of comparison is obnam, which to tell you the truth -- after all I've read, daily backups are actually a lot faster -- maybe 3-4x as fast.  The initial backup however was really slow. I don't however know how much compression of deduplication I'm getting from obnam.  Obnam is a little bit more Debian focused --- in fact it's only developed for Debian, so running it in not debian type distro's is kind of tricky, although it can definitely be done.  I'm still in process of comparing the two, and of course I've got to do a big wipe out of my original files and restore from the backup archive.  I haven't done this yet -- a backup isn't a backup until you've had to do a restore IMO.  I'd be interested in hearing you're experience.

Thanks for the info! I tried a test of borg against my Steam folder last night and you weren't kidding. It compressed the heck out of it, but it did take quite a long time to complete. Which level of compression were you using? I was using --compression zlib,6. I haven't really played with it much, thought, so I don't know how well it would work for me. Do you use one repo for everything or a separate repo for each folder? I'm not sure how I want to handle that - my current setup is to use pure rsync for my Steam folder and rdiff-backup for everything else.

---

### Post by kevdog on 2016-06-11
I'm using borg with these options:
-v --stats --compression lzma,9 --exclude-caches -p

It's probably slow for me because I'm using max compression, however it was always my intention with a backup of this type, that restoration wasn't going to fast. Because borg stores snapshots, and I have a lot of .vdi files, I wanted to be very conservative about the space taken up on the server. Frankly I'm finding out a 3TB drive as big as that seems, doesn't go too far when your snapshots can be potentially very large.  I just have one large repo.  I'm not sure if this is the most efficient or optimal strategy in terms of corruption or bit rot.

---

### Post by CharlesA on 2016-06-11
> **kevdog said:**
> I'm using borg with these options:
-v --stats --compression lzma,9 --exclude-caches -p

It's probably slow for me because I'm using max compression, however it was always my intention with a backup of this type, that restoration wasn't going to fast. Because borg stores snapshots, and I have a lot of .vdi files, I wanted to be very conservative about the space taken up on the server. Frankly I'm finding out a 3TB drive as big as that seems, doesn't go too far when your snapshots can be potentially very large.  I just have one large repo.  I'm not sure if this is the most efficient or optimal strategy in terms of corruption or bit rot.

Ah ok. Do you know what your IO is for borg? I checked with iotop and it was averaging 10MBps, but I'm also using all the CPU on the box, so I don't know if that is the speed I should expect or not.

I can totally understand where you are coming from.. I've been doing rdiff-backup on some qcow2 files for some VMs and it takes FOREVER to copy.

From what I've read, this should check for bitrot and whatnot because it verifies hashes and checksums.

```
borg check
```

---

### Post by tea for one on 2016-06-11
> **kaky951357 said:**
> hello,
i have a few problems whith my laptop, every time i use a terminal i kill my system

What exactly do you run in the terminal to kill your system?

It seems a bit odd that we generally use the terminal to repair our systems rather than destroy them?

---

### Post by kevdog on 2016-06-11
> **CharlesA said:**
> Ah ok. Do you know what your IO is for borg? I checked with iotop and it was averaging 10MBps, but I'm also using all the CPU on the box, so I don't know if that is the speed I should expect or not.


iotop on the server or client?

---

### Post by CharlesA on 2016-06-11
> **kevdog said:**
> iotop on the server or client?

I was testing it on the server, backing up to another local disk on the server. I was surprised at the low I/O, but thought it might be because I was maxing out the CPU and borg didn't have enough to handle deduplication efficiently. I've seen the same happen with Crashplan, but I don't know if that was the cause or not.

---

### Post by DuckHook on 2016-06-12
> **kevdog said:**
> iotop on the server or client?

> **CharlesA said:**
> I was testing it on the server, backing up to another local disk on the server. I was surprised at the low I/O, but thought it might be because I was maxing out the CPU and borg didn't have enough to handle deduplication efficiently. I've seen the same happen with Crashplan, but I don't know if that was the cause or not.

*cough* *cough*
Might I suggest that, to the extent that Borg could possibly be a solution for the OP, great. But please let's not lose sight of the OP's original problem.:)

---

### Post by alain.roger on 2016-06-15
1. AFAIK -z is for compressing data before transferring them and then data is uncompressed again...so it is just to reduce transfer time, not to save space on drive (I already asked this question in this forum)
after a while i found that "--compress --compress-level=0" could be used but i saw no real "compression" with or without this option too (i tested it with a bunch of text files and avoiding already compressed files like images or bin/zip)

2. Deja Dupe was my first try, but after people were complaining they were not able to restore backuped data, i moved on something else.

3. I agree with you that a backup is a 1 single shot synchronization operation, but i dislike that idea that damaged source data in a scheduled synchro, result in a damaged version in target directory.

---

### Post by CharlesA on 2016-06-15
> **alain.roger said:**
> 
3. I agree with you that a backup is a 1 single shot synchronization operation, but i dislike that idea that damaged source data in a scheduled synchro, result in a damaged version in target directory.

I use rsync and rdiff-backup in this way. The idea is to have versioned backup, so in case a file is corrupted, you can restore an older version of that file. This can be done with rsync and hard links or with the diffs that rdiff-backup creates. I do not see rsync as a "sync only" tool, even though "sync" is in the name as you can do a whole lot more than just sync files. If you add the [--link-dest switch]("http://linux.die.net/man/1/rsync"), for example, rsync will create hardlinks of files that haven't changed in the desination. That works wonders for doing incremental backups. :)

---

### Post by Kermit Charles on 2016-08-13
Thanks Y'all;

And, Duckhook, thanks for the "How-To-Geek" for Déjà Dup user instruction. I have two questions.

1. I'm wanting to test multiple Linux Distros which include several Ubuntu variations, but also Debian, Linux Mint, and Fedora; but, no commercial OS's. So, obviously the need for cross platform backups. Can one backup program sync between all these OS's? And if not which OS should I drop from this list and test on another PC.

2. The PC I’m using is a Lenovo ThinkCentre-A70, 3.7 GiB RAM, Pentium(R) Dual-Core CPU E5500 @ 2.80GHz × 2 CPU, 64bit OS, and 500 GB SATA HD. I have a ton of ATA HD's one of which is an empty 400 GB which I hung in the extra HD bay. This second HD is where I want to put the multi OS /home dir with OS specific subdirectories. 

Am I asking too much in this reply? 

Right now I'm using a 126GB USB stick and doing "copy" for all the directories for two OS's Ubuntu 15.04 and Linux Mint 17.

Thanks
Joe (aka Kermit Charles)

---

