---
title: "what happened to folders in my External HD? can i get them back?"
date: 2008-03-17
forum: General Help
---

### Post by spandanj on 2008-03-17
Hi, [screenshot attached]

I have run into BIG TROUBLE. some folders on my external HD are "missing" / inaccessible. I use the HD for downloading torrents directly. I always mount/unmount properly. also, in windows. Although, since i live on a shitty island called Dominica, the power goes out, may be, once every 2 days during which the torrent downloader deluge gives me error, obviously. so i close deluge-->unmount HD-->turn of HDf-->turn ON-->mounted-->run deluge again. it continuous the torrents, no problem.

NOW, however, i got this BIG problem out of nowhere. the power didn't even go out when this happened. i lost half of my folders--CAN'T OPEN THEM. anyway, to get those folders back??? THere has got to be a way...has to be. I need those folders.

Take a look at the attached [B]screenshot. 
[/B]
I read [http://ubuntuforums.org/showthread.php?t=576037](http://ubuntuforums.org/showthread.php?t=576037) - it didn't help.

Please help me.:(

---

### Post by Rocket2DMn on 2008-03-17
What error does it give you when you try to open the folders?  Can you access them from terminal with the "cd" or "ls" commands?

---

### Post by LeAstrale on 2008-03-17
its because of too much pr0n on the pron HD ;)

sry i just couldn't help it. I unfortunately don't have any solutions for you.

/Astral-1

---

### Post by Rocket2DMn on 2008-03-17
> **astral-1 said:**
> its because of too much pr0n on the pron HD ;)

sry i just couldn't help it. I unfortunately don't have any solutions for you.

/Astral-1

Glad you threw that out there, I was trying to play it cool.
:lolflag:

But really, it's not our business.  We'd be glad to help you out as best we can, spandanj.

---

### Post by LeAstrale on 2008-03-17
> **Rocket2DMn said:**
> Glad you threw that out there, I was trying to play it cool.
:lolflag:

But really, it's not our business.  We'd be glad to help you out as best we can, spandanj.


i would be even happier if you shared some of the good stuff ;)

---

### Post by spandanj on 2008-03-17
haha, not that I am a "40-year-virgin" or adult, but I didn't expect the "porn" issue to come up so quickly....haha. (i never store my porn on an External;))

1. when i click on it, NOTHING HAPPENS. no prompt, no error. nothing.
2. i can't access via terminal 

[spandan@spandan-laptop:/media/spandanHD$ cd camera movies [or cd camera_movies]
bash: cd: camera: No such file or directory]

-So, what do i do? (besides redownloading all the porn?:-k:cry:)

NO, SERIOUSLY, I need that data .... its important. help.

---

### Post by spandanj on 2008-03-17
> **astral-1 said:**
> i would be even happier if you shared some of the good stuff ;)

no, sorry bro, no porn, sorry. just important data--needs to get it back. Y'ar help shall be greatly appreciated.

---

### Post by spandanj on 2008-03-17
> **Rocket2DMn said:**
> Glad you threw that out there, I was trying to play it cool.
:lolflag:

But really, it's not our business.  We'd be glad to help you out as best we can, spandanj.

....I hope so, (look at your four cups, one glass of ubuntu experience).....
....I am a novice beans...i dont know how to solve anything in ubuntu.

---

### Post by Rocket2DMn on 2008-03-17
What filesystem is the drive formatted in?  In the directory from which you can't access subdirectories, please post
```
ls -l
```
Feel free to change the file/folder names, but leave the other data intact, please.

---

### Post by spandanj on 2008-03-17
tried using **Terminal.**

take a look at the **screenshot**

---

### Post by spandanj on 2008-03-17
> **Rocket2DMn said:**
> What filesystem is the drive formatted in?  In the directory from which you can't access subdirectories, please post
```
ls -l
```
Feel free to change the file/folder names, but leave the other data intact, please.

Here you go. take a look at the_ screenshot attached._
ps. I can choose to trust you...looking at my folder names.

---

### Post by Rocket2DMn on 2008-03-17
OK I still need to know what filesystem the drive is in, can you please post the output of
```
sudo fdisk -l
```
Identify the correct drive for me if you can.  You don't need to post a screenshot, just copy and paste the output here.

---

### Post by spandanj on 2008-03-17
spandan@spandan-laptop:/media/spandanHD$ sudo fdisk -l
[sudo] password for spandan:

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6008    48259228+   7  HPFS/NTFS
/dev/sda2            6009        9394    27198045   83  Linux
/dev/sda3            9395        9546     1220940    f  W95 Ext'd (LBA)
/dev/sda5            9395        9546     1220908+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10d6c778

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
spandan@spandan-laptop:/media/spandanHD$

---

### Post by spandanj on 2008-03-17
its ntfs - so i can use it on my windows too.

---

### Post by ad_267 on 2008-03-17
You could try running checkdisk in windows on that drive.

I think theres a linux equivalent fsck but I don't know if that works for ntfs, someone else will know what's best to use. But I managed to mess up an ntfs file system once when my pc got turned off while copying some data and ubuntu wouldn't mount the drive at all. Running checkdisk fixed that for me.

---

### Post by Rocket2DMn on 2008-03-17
Agreed, boot into windows and run chkdsk on the drive.
There is a program called ntfsfix in the ntfsprogs package, but I would prefer to run the check under windows since ntfs is their native file system.

---

### Post by spandanj on 2008-03-17
agreed. I will run check disk in windows today. Hopefully, that solves it. I ll post what happens.

Thank you. your help is Much Appreciated. just knowing someone's out there to answer is such a relief...thank you, again

---

### Post by spandanj on 2008-03-20
UPDATE:

I ran chkdisk in windows xp.  the chkdisk got stuck in phase 4. tried it twice. both times it took few hours and then it got stuck in phase 4. 

As of now, the folders that i could see in the hard-drive in form of "letter files", i can't even see them anymore. Only half of the folders are there.


any solution?

---

### Post by Rocket2DMn on 2008-03-20
Sounds like the hard drive is going bad.  First, you should recover everything from it that you can by dragging as much stuff as you can to another hard drive.  You can also try using "ntfsfix" in linux like I mentioned above.
A brief search revealed this thread which might help you recover some of the data: [http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)
Good luck.

---

