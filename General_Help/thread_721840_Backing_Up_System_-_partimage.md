---
title: "Backing Up System - partimage"
date: 2008-03-11
forum: General Help
---

### Post by adammc on 2008-03-11
Hi guys,

I'm a bit of a linux newbie and have just installed all my fav programs and have the system running just as a like it too.

What is the best method to backup the entire system as is so if something goes wrong I can get it back to its current state?

I have heard of partimage, is this the best tool for the job?
Is it a complicated task to restore the system?

Or should I be using another method?

---

### Post by adammc on 2008-03-11
I forgot to mention....

Im running a dual boot with XP, will this be also achievable with partimage to accomplish a successful restore?

---

### Post by logos34 on 2008-03-11
> **adammc said:**
> 
I have heard of partimage, is this the best tool for the job?
Is it a complicated task to restore the system?

Or should I be using another method?

That's what I use for backup of root partition (~weekly).  I also store all .debs on AptOnCD dvd, and backup /home (on a separate partition) into tar.gz file.  

[This page]("http://www.partimage.org/Partimage-manual_Usage") should answer your questions.  (You have to work from a live cd).  The most common problems seem to be getting the path to the backup/restore file correct and restoring from compressed file (but if you use the default split option of ~2 GB file chunks, it isn't an issue).

---

### Post by logos34 on 2008-03-11
> **adammc said:**
> I forgot to mention....

Im running a dual boot with XP, will this be also achievable with partimage to accomplish a successful restore?

Partimage support for NTFS is still experimental, so no.  I've tried it and windows boot froze at blue welcome screen.  (altough the problem may be with windows--it does not respond well to any changes in its environment).

---

### Post by froy02 on 2008-03-11
If you are dual booting with XP, the best back up is Acronis back up and restore disk.  If you are using Seagate or Maxtor drives you can download the utility from Seagate/maxtor website, free.  
What it does is make an image of your entire disk and saves it to a file.  When you restore, it restore your whole hard drive to the state when you back it up including your windows and linux installation.
My windows and linux installation use about 18 gb and when backed up it is about 9 gb. 
You can restore to another drive in case change the hard drive.  It takes about 10 minutes to back up and 10 minutes to restore.
After restore all you have to do is boot up.

---

