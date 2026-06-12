---
title: "[SOLVED] Accidentally deleted external USB HDD contents"
date: 2007-09-26
forum: General Help
---

### Post by T3KN33K on 2007-09-26
So the story goes like this... I have a 500gb external hdd which I store all of my media and whatnots on.  Music, movies, appz, games, etc.  Basically, I kept my internal primary hdd as clean as possible; I would install programs I used on it, and thats about it.  All media was kept on the external, so that in the event of some sort of OS failure, or just that I was in the mood to wipe my internal drive and start over, I would retain all of my prized media. 

Today a friend describes to me a problem with his computer that I assessed as a burnt out PSU.  Luckily for him, I upgraded my own PSU just days ago, and thus had a functional spare.  I went over to his house to replace his PSU, and also to wipe his system and give him a fresh install of (sorry, he's not the Linux type) XP.  I brought along with me my external HDD so that we could save what he needed to, as well as to save a copy of his driver installers, and reinstall his commonly used software, such as MS Office (for which I had copies of already on my hdd).  Long story short (assuming that ship hasn't yet sailed :lolflag:), upon entering the partition utility in the XP boot disk, I accidentally chose to wipe MY hard drive (which was still plugged in via its usb cable) rather than his internal hard drive.  The thing is, it wasn't just the contents that were wiped, it was the entire partition, leaving me with 500GB of unpartitioned space.  

Now, although I know that there are options for recovery utilities out there, I have no experience with any of them.  In the last 20 minutes, I have done some research into what exactly those options are, and I am still kind of unsure.  The main issue is that I have ~300gb of deleted data, and my only other HDD is 80GB.  From what I read, it seems that I have to copy the recovered data to a disk other than that from which I am attempting to recover data.  The only exception to this rule that I have seen is a vague anecdotal reference someone in a forum made to recovering the lost data to an image file on the same disk, which, if possible, I believe would be my only option (other than tracking a 300gb+ drive to borrow from someone).  

SO....  if anyone has any suggestions, it would go much, much appreciated.  If there is any way I can avoid starting my collection from scratch, this side of paying a tech shop to do it, PLEASE let me  know!  Thanks in advance...


EDIT: Also, not sure if it matters or not, but the files deleted were primarily: 

[LIST]
[*]<AUDIO> .mp3, and .wma;
[/LIST] 
[LIST]
[*]<VIDEO> .wmv, .mpg, and .avi;
[/LIST] 
[LIST]
[*]<SOFTWARE>; .rar, .zip, .daa, .iso and .exe
[/LIST]

---

### Post by T3KN33K on 2007-09-26
<bump>

---

### Post by Wolki on 2007-09-26
Take a look at this: [http://www.linux.com/feature/56588](http://www.linux.com/feature/56588)

I had something similar happening to me many years ago, and didn't find a working solution then. Backups would've been niche :-/ Good luck!

---

### Post by T3KN33K on 2007-09-29
So, here's an update on my progress....  If I understand things correctly, a "quick format" does **not** remove any data from the disk.  Instead, it just labels that disk space as "available", so until anything else is written over that particular sector of the drive, whatever information was once visible there, is still physically there.  

The problem with that is, typically the best solution would be to image the drive with the lost data, save that image to a different disk, and then attempt to recover the files from that image.  Which means I would need 2 more partitions of the same size as my lost data (~300gb).  Since my internal 80GB hard drive falls just a tad short of the ~1TB of space I would need to complete the recovery, I looked into paying a professional recovery shop to take a crack at it. Upon finding out that it would cost $200+ to do so, I realized that my meager student budget could be better spent elsewhere than on ensuring the retention of my music and movies :popcorn:.  SO...  I found this community page [https://help.ubuntu.com/community/DataRecovery#head-999ba4e87a733741c3eec6134fea940b01495a1a](https://help.ubuntu.com/community/DataRecovery#head-999ba4e87a733741c3eec6134fea940b01495a1a).

This, along with several other articles I came across while googling the issue, have lead me to the (hesitant) belief that because 1) my hardware is in perfectly operable condition, 2) no data has been written on top of the deleted data, and 3) I do not have any ***crucial*** data on the disc, I should be able to safely recover the data to the same disk with minimal loss, and without losing anything that is irreplaceable.

So, at the suggestion of the above listed ubuntu community, I installed testdisk, and ATM i am researching how exactly to best proceed with the software.  

If anyone has any personal experience with a similar issue, or with the software, or has a link to a documented account of either, or any other info/comments/suggestions, it would be much appreciated.  Thank you!

**EDIT:**  Also, it seems to me that *recovering* data, by definition, implies restoring data that has either been corrupted, or that is stored on malfunctioning hardware.  This is unique from my particular situation, which involves *undeleting* files which have only been removed from the list of files in a folder, and not actually _deleted_.  *Undeleting* is apparently a much easier procedure than *recovering*.  That said, I'm still hunting for an effective way of doing so with my limited hardware.......

---

### Post by T3KN33K on 2007-09-30
SOLVED!

So, its 4:30 in the morning here right now, and I just called and woke my friend (the one whom was partially responsible for my formatted drive :mad:) to let him know that everything is back to exactly the way it was, without deviation, and without expense.

What I did was this:
[LIST=1]
[*]Install testdisk.  Forget exactly how I did this at this point, but I believe it may have just been from apt-get, as in "sudo apt-get install testdisk"
[*]Run testdisk simply by typing "testdisk" into terminal, and maximizing the window.
[*]Program auto-detects connected drive partitions....  highlight the relevant drive and hit enter.
[*]Select the file system that the drive was BEFORE the accident.  In my case, Windows filesystem. (In particular, FAT32, although this is not specified in the program at this stage.)
[*]Highlight "Analyze", hit enter.
[*]...Run scan, wait....
[*]At end of scan, highlight "Search!" for "deep search".
[*]When search completes, hit enter, or L to view the files found.
[*]Highlight and select "Rebuild Partition Table"
[*]..after confirming, the program will explain to you that it is necessary to have a boot sector on the drive, regardless of whether or not the drive is to be booted from.  So, select "Rebuild Boot Sector"
[*]Restarted machine, crossed fingers, and Voila!  Everything is back the way it was.
[/LIST]

So, what I have learned from this incident is:
[LIST]
[*]If you accidentally delete anything from a single file, to an entire partition, DO NOT write ANYTHING to that drive if you want any hope of recovering it.
[*]Anything deleted or quick-formatted is RECOVERABLE in most circumstance, provided you do not write anything else to the disk afterwards.  The data in most cases is NOT deleted from the disk, but rather the sectors are marked as "available", and data will reside dormant until overwritten.
[*]With enough time and effort, you can usually do pretty much anything the pros can without shelling out hundreds.
[*]When formatting a drive, ALWAYS triple check the drive label, size, mounting position, etc. to ensure that you have selected the right drive - Although such actions are seemingly recoverable, it is undeniable that it will be a MONSTROUS pain in the ***.
[/LIST]

---

### Post by richard@aboutavatar.com on 2008-04-14
:KSGreat post my friend! 

I used all the steps you used on my eek i dread to name it, Vista Notebook with all my files on a 320gb external drive and success.....

i had done exactly what u did, mistakenly quick formatted it while helping someone fix their machine.

thank you for bothering to post all your findings!

richard
:KS:KS:KS:KS

---

### Post by az on 2008-04-14
FYI, even a long format preserves the data.  A long format does a read-only test.  A format to ext3 can do a read-write test, but that is not the default.

There is no format tool for NTFS that overwrites the data.  You need to delete the data by hand (using linux, for example) to get rid of data from a hard drive in widnows.

---

