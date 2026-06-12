---
title: "Files deleted... or not."
date: 2007-04-03
forum: General Help
---

### Post by NT4usB on 2007-04-03
When I plug NTFS external drives into my Ubuntu box (read only) I made some interesting discoveries.

Files deleted off the NTFS drive via Windows were visible and intact when viewed on the Ubuntu box.

I networked my Mythbox and poked around it from my XP box.
I could view, copy, and play (mythtv recordings) files deleted off shared ext3 drives in my Ubuntu box when viewed from my XP box. 

$ locate didn't find them anywhere on the machine, but they were there.
cd'd to the folder where windows sees them... nothing.

Copied them to another folder on the Ubuntu box and locate found them.

Are there *really* hidden files/folders in Linux that can't be seen by the OS?

I know Windows has them, does Linux?

I haven't actually searched for deleted files to see if this works for all files on the Ubuntu box but for sure the deleted recordings were there.

---

### Post by kidders on 2007-04-04
Hi there,

> **NT4usB said:**
> locate didn't find them anywhere on the machine, but they were there.The "locate" database is relatively infrequently refreshed ... you can't really rely on it to find anything that isn't part of your system (and hence always there, and in the same place). On most Linux systems, the database is typically updated 24-hourly, provided the machine is switched on at the right times.

Anyhow, there are a few possible explanations for your strange filesystem behaviour, bearing in mind (a) that many "deletions" aren't really deletions at all (ie trash bins), and (b) that deleting a file only removes references to it from FAT/Inode tables, rather than actually wiping any data...[LIST]
[*]You may have dismounted your filesystems uncleanly, causing some changes to fail to be written out to disk. [SIZE=1][Reasonably likely][/SIZE]
[*]It's conceivable that a filesystem implementation could elect not to trust filesystem metainformation, and go wandering around a disk for data instead, in search of files. Such behaviour would entail a serious performance penalty, but could result in the resurrection of recently deleted files. [SIZE=1][Unusual][/SIZE]
[*]Rarely, filesystem implementations can just be plain faulty. [SIZE=1][Unlikely][/SIZE]
[*]You might be confused. [SIZE=1][????][/SIZE][/LIST]This isn't a definitive list ... it's just a collection of possibilities that spring to mind. I've never actually seen this happen, myself.

> **NT4usB said:**
>  Are there *really* hidden files/folders in Linux that can't be seen by the OS? I know Windows has them, does Linux?Naturally, files an OS can't see are invariably malicious in nature, since no operating system would deliberately store data in a way that it couldn't subsequently recall. What you're describing is possible on most filesystems, with most OSs (including Linux), but is of no practical use, unless your up to mischief!

---

### Post by NT4usB on 2007-04-04
> **kidders said:**
> Hi there,

The "locate" database is relatively infrequently refreshed ... you can't really rely on it to find anything that isn't part of your system (and hence always there, and in the same place). On most Linux systems, the database is typically updated 24-hourly, provided the machine is switched on at the right times.
I run sudo updatedb before I use locate
> 
Anyhow, there are a few possible explanations for your strange filesystem behaviour, bearing in mind (a) that many "deletions" aren't really deletions at all (ie trash bins), and (b) that deleting a file only removes references to it from FAT/Inode tables, rather than actually wiping any data...[LIST]
Which is why I believe Linux can see the files on a NTFS drive. It doesn't read the table the same way Windows does. I've seen this table on a NTFS drive when viewing via Linux... it's nothing more than a textfile.
> 
[*]You may have dismounted your filesystems uncleanly, causing some changes to fail to be written out to disk. [SIZE=1][Reasonably likely][/SIZE]
Probably. The mythbox has been pretty much abused. It was my first foray into Linux
> snipp...
[*]You might be confused. [SIZE=1][????][/SIZE][/LIST]
No doubt, but that's another issue..!!
> This isn't a definitive list ... it's just a collection of possibilities that spring to mind. I've never actually seen this happen, myself.

Naturally, files an OS can't see are invariably malicious in nature, since no operating system would deliberately store data in a way that it couldn't subsequently recall. What you're describing is possible on most filesystems, with most OSs (including Linux), but is of no practical use, unless your up to mischief!

Really old article on Msoft hidden files:
[http://www.microsuck.com/content/ms-hidden-files.shtml](http://www.microsuck.com/content/ms-hidden-files.shtml)

---

### Post by kidders on 2007-04-05
Hey again,

> **NT4usB said:**
> I run sudo updatedb before I use locateKewl. :-) Doing that can be time-consuming, but it's nice how quickly results come back from searches.

> **NT4usB said:**
> Really old article on Msoft hidden files:
[http://www.microsuck.com/content/ms-hidden-files.shtml](http://www.microsuck.com/content/ms-hidden-files.shtml)Hehe... these seem to be examples of cases where the Microsoft UI is hardwired to ignore certain things. You should be able to see any such files using older MS operating systems (or any Linux), since they're not really hiding ... they're just being "overlooked". (Isn't MS strange!) When files are *really* hidden (like rootkits can do), there should be very little evidence of their existence.

I have to say, your problem raises some interesting security issues. Is that of concern to you, or is your PC a home desktop computer?

---

### Post by NT4usB on 2007-04-05
> **kidders said:**
> ...Hehe... these seem to be examples of cases where the Microsoft UI is hardwired to ignore certain things. You should be able to see any such files using older MS operating systems (or any Linux), since they're not really hiding ... they're just being "overlooked". (Isn't MS strange!)....

The same is true for deleted files since they really aren't removed from the drive.
So an OS that doesn't respect MS hardwired ignorance should see deleted files. 

> 
I have to say, your problem raises some interesting security issues. Is that of concern to you, or is your PC a home desktop computer?

No concern, just a curiosity...
I see lots of *'I deleted* (insert important filename)* how do I get it back?'* posts.
If recovery were as easy as just hooking it up to another OS, could make some folks really happy.
MythTV users are forever going on about 'how do I undelete a recorded program?'

---

