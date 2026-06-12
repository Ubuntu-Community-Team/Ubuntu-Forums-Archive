---
title: "Catastrophe! Urgent help required!!"
date: 2007-01-04
forum: General Help
---

### Post by Sutur on 2007-01-04
I have two identical Seagate 250GB hard drives both formatted as ext3.

Drive 1 (Storage) is physically installed inside my computer.
Drive 2 (Backup) is plugged in via an external hard drive that I turn on only to back up what's on the storage drive.

Yesterday, I realised that ext3 uses an overhead, and there was about 12/13GB of unused/wasted space. So I decided that I would format the drives to reiserfs while retaining the data.

Last night I formatted the Backup drive to reiserfs, leaving the Storage drive intact. I then began copying files from the Storage drive back onto Backup using the drag & drop method in nautilus.
It reported about 4-6 hours of copying time for about 230GB of unrestorable data so I left it to copy while I got some sleep.

The next morning a number of things happened:
1. The computer had frozen, the Storage disk light was constantly lit.
2. I restarted the computer, first of all it made a series of beeps at bootup (which the motherboard manual did not cover).
3. When I turned it off and back on again, it decided to load with no problems until linux started to complain about the root filesystem having problems. The filesystem checks failed and I was told that I should fix it manually (?). (If someone could tell me how to recover this data and make it available here please tell me.)
4. I did manage to enter X-windows eventually, and when I tried to open the Storage drive I was absolutely mortified to discover that **nothing** was there - the disk was 'empty'.
5. The Backup drive had *some* files copied on to it, but nowhere near half.

All I want right now is to make the Storage drive work. I just want my data back. I am convinced there is an easy solution but there are so many factors at hand that I don't know where to begin diagnosing this Storage drive, and even if I should!

I cannot afford to lose the data on my Storage drive. If anyone has the compassion to help me I would be greatly in their debt - I'm begging someone to help me *please!*

---

### Post by riven0 on 2007-01-04
Man, that sucks. I'm not really sure what happened, but it's going to be pretty hard to recover that data. Here are some sites you should look over. The programs listed in the first link are known to work, but they are difficult to use. If you have no luck there, try the other links. Good luck.

[How to recover deleted files after you accidently wipe your hd]("http://servers.linux.com/servers/06/08/21/1558230.shtml?tid=119&tid=13")

[Linux or UNIX Recover deleted files - undelete files]("http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html")

[Deleted files recovery howto]("http://e2undel.sourceforge.net/recovery-howto.html")

---

### Post by Sutur on 2007-01-04
But they weren't deleted...I didn't delete anything.

---

### Post by riven0 on 2007-01-04
> **Sutur said:**
> But they weren't deleted...I didn't delete anything.

But they are gone, right? Do you have another comp to hook the external drive up to, just to make sure the files have really disappeared? 
Did you check the your entire home folder on Ubuntu? Perhaps they transfered over there without leaving a copy on your external hd. 

Otherwise, they had to have been deleted somehow. It makes no sense otherwise. It does sound strange, though. :confused:

---

### Post by quartzy on 2007-01-04
It sounds to me like you corrupted the area of your harddrive that specifies where everything is located, if that is the case you do need to try and 'undelete' the data.  I would suggest not commiting to any form of trying to recover without trying afew first though..

I may easily be mistaken..

---

### Post by koenn on 2007-01-04
I think you should start at
```
The filesystem checks failed and I was told that I should fix it manually (?).
```
I mean : you're told that something is wrong with your filesystem, and it's so bad that the system couldn't fix it automatically (usually, it can). 
It says 'manually' because it will need you to give answers to questions that it can not guess the answer to. 

checking is done with```
 fsck -r
```
it should not be run on a read/write filesystem. If you're data is on a seperate partition, you can unmount it and remount it readonly. 
If everything is on one partition; that's going to be harder - mmaybe setting the partiotion to mount readonly (ro) instead of rw in /etc/fstab helps. 
Also, you better run this vrom a console, eg in maintenance mode (no GUI, Gnome, ...)

---

### Post by steve.horsley on 2007-01-04
I take it taht your storage drive is not your system root drive. If you are lucky, the corrupt system simply isn't mounting the storage drive (in which case you will see the empty mount-point folder instead). Check with the command **mount** or **df**. If this is the case, you should be able to mount the storage drive manually and then perform the copy to the backup drive. If your system is really screwed. maybe a live CD will be able to mount hte drives and copy the data.

P.S.
I would be tempted to do command-line copy commands, not nautilus ones, since nautilus has proved problematic once already.

---

### Post by Sutur on 2007-01-04
Bless you all for your help. It's really nice to see so much charity in the world.

This is truly bizarre, but the following events have come to place:

1. I removed the Storage drive, and put into the external case that normally holds the Backup drive. I then used a Damn Small Linux live cd to try and read that = no luck.
2. I tried booting into windows, then using multiple programs to read the ext3 Storage drive from there = no luck.
3. I tried booting into linux with the drives in their original places, just for luck (even though I know even activating a potentially damaged hard drive is beyond stupid).

The system began checking the root drive (just an old 20GB IBM) and found a number of problems. At around 80% of the check, the system came to a halt, and I was forced to turn it off.

I gave it one, last, final bootup. To my surprise the system loaded perfectly. My storage drive is intact, no files are corrupt and it's working perfectly.

However, I am not convinced that this is the end of the threat. Since I am now in a position where I can back up my data, I'm not sure whether I should given the unstable results of attempting it in the past. I have no option but to take my chances now and back up my data using command line interface as previously suggested. I will report the results afterwards.

Thank you.

---

### Post by smoker on 2007-01-04
glad you got this sorted. maybe you can check the log files for a clue perhaps for how it happened.

i usually use the hard drive manufacturers apps for copying drive to drive, if you want to give that a try check the website of your hard drive maker

---

### Post by mdurham on 2007-01-04
Sutur, I'm glad that you resolved it too. Just one point. DON'T EVER use Nautilus for copying a large amount of files. It's crap! Use rsync and sleep better at night. I had problems using Nautilus over a year ago so I filed a bug report (others have too) and it seems nothing has been fixed. I got a request from someone dealing with the bug reports just the other day and he asked me the name of the file that caused the problem. He must be joking, ALL files cause a problem to Nautilus. Anyway as I couldn't supply the name he said he couldn't fix it.
USE RSYNC, it just works.
Cheers, Mike

---

### Post by koenn on 2007-01-05
> **Sutur said:**
> 
The system began checking the root drive (just an old 20GB IBM) and found a number of problems. At around 80% of the check, the system came to a halt, and I was forced to turn it off.

I gave it one, last, final bootup. To my surprise the system loaded perfectly. My storage drive is intact, no files are corrupt and it's working perfectly.


Since the system apparently did not complete it's fsck (only 80% ?) i'd let it check the filesystems once again, (and again, ...) untill all problems are fixed. If you don't, you risk problems showing up again in the future, and you probably don't want a 2nd catastrophe. 
You can do this by rebooting and telling the system to do fsck at boot : 

```
shutdown -r -F now

```

Also, as others suggest, i wouldn't use nautilus to copy such a large amount of data. try cp or rsync : less overhead, so less change the system will hang and cause trouble again.

---

### Post by 3rdalbum on 2007-01-05
What goes for Nautilus also goes for Konqueror in that regard, I'm afraid.

I've also found that copying tends to go better if you copy smaller batches of files at a time. No idea why. If you don't want to physically be there while the files copy, you could set up a simple bash script to do one copy command after another.

---

### Post by koenn on 2007-01-05
> What goes for Nautilus also goes for Konqueror in that regard, I'm afraid.
... and any other file browser, i suppose. Come to think of it : you're copying hundreds of filesd / millions of bits from one disk to another. That already sounds like quite a bit of work to me. Now, if you do it through a file browser, you're asking your system to run an additional program (while it's already busy handling all those files), that application wants to keep track of the copy process (just to show you that process bar) so it will be busy getting feedback and translating that into a progress %, and as file browsers are espected to show an up to date representation of the files and folders on the disks, it will be reading a continously changing disk (you're copying files, right) ... Maybe it just gets too much ...

I find rsync excelent to  copy large ammounts of files. It only "copies" the difference between the source and the destination. That means you can easily run it 2 or 3 times for the same "copy job" : the second time (and following) times , it will only copy whatever files were missed in previous attempts. If it breaks of in the middle of a job, you can run it again and it will only deal with what hasn't been copied before. Great tool. one can imagine a nightly copy job with a script that runs rsunc 5 times in a loop (or until completed without errors), the next morning you can do a quick check by running rsync once more - if the previous rsyncs were succesfull, it will have nothing to sync anymore - takes a fraction of a second.

---

### Post by Sutur on 2007-01-05
Hello all, thank you all again for the continued support and charity. Some good news - both the Storage & Backup drives are now formatted as reiserfs, and are an exact mirror of each-other.

The data I thought lost is now quite secure and safe. I used the command line cp -R command and killed all x-win processes. Thanks for the info on rsync, I will certainly be using it in future :-)



So anyway, I'm back with (what I understand to be) the report of the errors fsck was giving me at bootup. They are still cropping up, so I just opened

```
/var/log/fsck/checkfs
```

And the details below are the contents of this file.

```
Log of fsck -C -R -A -a 
Sat Jan  6 12:46:27 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Bad magic number in super-block while trying to open /dev/hdb1

/dev/hdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65, 436:69/20
  , 437:73/64, 438:20/69, 439:6d/73, 440:69/6b, 442:73/20, 443:69/6f
  , 444:6e/72, 445:67/20, 446:ff/6f, 447:0d/74, 448:0a/68, 449:44/65
  , 450:69/72, 451:73/20, 452:6b/6d, 453:20/65, 454:65/64, 455:72/69
  , 456:72/61, 457:6f/2e, 458:72/ff, 459:ff/0d, 460:0d/0a, 461:0a/44
  , 462:50/69, 463:72/73, 464:65/6b, 465:73/20, 466:73/65, 467:20/72
  , 468:61/72, 469:6e/6f, 470:79/72, 471:20/ff, 472:6b/0d, 473:65/0a
  , 474:79/50, 475:20/72, 476:74/65, 477:6f/73, 478:20/73, 479:72/20
  , 480:65/61, 481:73/6e, 482:74/79, 483:61/20, 484:72/6b, 485:74/65
  , 486:0d/79, 487:0a/20, 488:00/74, 489:00/6f, 490:00/20, 491:00/72
  , 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72, 497:00/74
  , 498:00/0d, 499:00/0a, 506:bf/cb, 507:cc/d8
  Not automatically fixing this.
/dev/hda3: 17015 files, 741798/1078311 clusters
fsck died with exit status 8

Sat Jan  6 12:46:32 2007
----------------

```

/dev/hda1 is the root file system,
/dev/hda2 is the swap partition,
/dev/hda3 is is a windows (fat32) partition, which isn't really of any concern to Linux anyway,
/dev/hdb1 is not ext3 anymore, which explains the first error message.

BUT, the problem that's really holding me back has not appeared in the log file above.
I'm not a Linux guru despite the amount of time I've used it, and I'm not sure exactly where to look for the log file that will tell me what's *really* going on.

I'm going to shutdown with the switches suggested before by koenn:

```
shutdown -r -F now
```

More news soon, and many, many thanks again :)

---

### Post by louieb on 2007-01-06
Nice to see you got your data back. Now that you have changed the file system types on the two drives check /etc/fstab and see if the type has been changed there also.

---

