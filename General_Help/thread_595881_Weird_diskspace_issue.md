---
title: "Weird diskspace issue"
date: 2007-10-29
forum: General Help
---

### Post by sebbouckaert on 2007-10-29
Hi,

Yesterday afternoon, I've experienced a sort of weird crash with my Gutsy. First of all, I'm running on a HP pavilion desktop system, dual boot XP/Ubuntu. The system has a dual core 3ghz processor (V // V technology), 1 gb of ram, and NVIDIA graphics (just over 1 year old PC)

Strange behaviour started when I tried to copy a large video file from my local disc to a smb share on another PC using Nautilus. This, obviously took some time to copy. Because I wanted to edit these video files in Windows I started up vmware-server to boot up a virtual XP. Being to impatient, I saw that this was obviously more than my box could handle. While the whole system grinded to a massive slowdown, I noticed a constant HD read/write activity (swapping memory, I thought.)

After giving it some time, I managed to shut down the vmware-server and some other app's, and eventually I could give the PC a clean reboot. But then I noticed that my 40 GB ext3 partition was almost full, indicating a 98%  usage (leaving aproximatly 800 MB free) whereas before it had only 65% in use.

I tried to find out what happened, I checked and searched for recent files, checked the amount and size of recent log files, checked the size of the vmware virtual disks, but I could not find the reason why my disk was suddenly full. 

This morning I have replaced the partition with an older Gutsy image I backed up earlier (using Windows XP) I I am now back at a fresh install, and therefore can't post any additional info of terminal output. But does anyone have an Idea or similar experience of what might have happened here yesterday?

---

### Post by strungoutfan78 on 2008-06-07
I had the exact same issue and I have still not dealt with the headache of trying to fix it just yet.  I tried to move my vmware vista image from my /usr partition to my home partition because I noticed it was taking up quite a bit of room (about 16Gb).  During the process I cancelled the operation because it was just taking way too long.  I instead decided to delete the image because I no longer needed it anyways.  Even after deletion my /usr directory is now at a constant 96-98%.  I've looked at this from every angle, including the amazing FileLight program which shows me exactly what is where.  My /usr partition is 18Gb and only 6 are actually being used.  What happened to my other 12 GB?!?!?  

Unfortunately I, the lazy grasshopper, do not have a backup image to fall back on.  I wonder if this is a common occurance?  If so is it a Hardy bug/issue?  Or did my impatience eff-up my hard-drive?

---

### Post by sebbouckaert on 2008-06-07
> **strungoutfan78 said:**
> I had the exact same issue and I have still not dealt with the headache of trying to fix it just yet.  I tried to move my vmware vista image from my /usr partition to my home partition because I noticed it was taking up quite a bit of room (about 16Gb).  During the process I cancelled the operation because it was just taking way too long.  I instead decided to delete the image because I no longer needed it anyways.  Even after deletion my /usr directory is now at a constant 96-98%.  I've looked at this from every angle, including the amazing FileLight program which shows me exactly what is where.  My /usr partition is 18Gb and only 6 are actually being used.  What happened to my other 12 GB?!?!?  

Unfortunately I, the lazy grasshopper, do not have a backup image to fall back on.  I wonder if this is a common occurance?  If so is it a Hardy bug/issue?  Or did my impatience eff-up my hard-drive?

Wish I could help out, but as I said, I restored an backup image of my linux partition, so I don't know what causes this...

maybe check the /var/log directory?

---

### Post by strungoutfan78 on 2008-07-10
Ok, so I still haven't fixed the weird /usr partition being suddenly full when, what happens?  My root partition suddenly becomes 98% full.  Again, this is a 17 GB partition with about 1.7 GB in use but it says it is full.  Could my HD be fouled up?  I use ReiserFS, is this a common occurance with this FS?  All the journal replays check out and fsck returns no errors.

I've never had this problem with ext2 or ext3.  I use sbackup now to backup all my data.  How, if I decide to reformat my HD, would I go about restoring from these backups?  I'm not well versed in backup and recovery as you could probably guess from my first post.

---

### Post by strungoutfan78 on 2008-07-14
I found out what it was.  For some reason the 14 GB file I tried to delete from my /usr partition ended up in a hidden folder called /usr/.Trash-0.  I found a tip pertaining to this in the Sabayon forums so I checked it out.  Sure enough it was right on the money.

Strangely enough, though, my recent loss of space on my root partition was due to my new backup utility, sbackup.  I had it set to backup to my external hard drive mounted at /media/backup.  It was to create a weekly full and daily incrementals.  What I didn't realize was that if my external was not mounted sbackup was still creating backups, only storing them LOCALLY in /media/backup.

Needless to say I have removed sbackup and I think I'm gonna stick to rsync instead.  Hope this may help someone.

---

