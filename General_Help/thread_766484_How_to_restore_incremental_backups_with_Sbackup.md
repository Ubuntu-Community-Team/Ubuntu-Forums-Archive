---
title: "How to restore incremental backups with Sbackup"
date: 2008-04-25
forum: General Help
---

### Post by sostenible on 2008-04-25
Hi, Yesterday I accidentally installed 8.04 on top of 7.10 (where I had all my freelance activity documentation).

Luckily I had performed with Sbackup incremental backups (daily) and full backups (monthly) of many of my /home directories.

However, after changing permissions, I came across this problem when attempting to restore:

- If I only restore the latest .inc backup I miss most of the information

- If I restore the latest .ful backup (20 days old) + the next 19 .inc backups I get all the information but I also get tonnes of files called "status_previous_to_date_backup" (or similar) in each restored directory.

Can anyone tell me how should I proceed to do a clean restore of the incremental backups that I have?

Many thanks (I need this for my work!!)

---

### Post by 2CV67 on 2008-08-22
I don't have this problem yet, but I just installed sbackup & performed some trial backups.
The backups work fine, but, like sostenible, I can't see how I would ever get a complete up-to-date restore from several incremental backups, each with fragmentary information.

I assume it must be possible, or nobody would be using sbackup, would they?

Did anybody reply, or could somebody help please?

Thanks!

---

### Post by B0rat on 2009-02-04
Sorry for the late reply to this thread but I thought I would follow-up here.

I have recently needed to restore from sbackup and encountered a similar problem. I had to restore the .ful backup first and then each snapshot sequentially. This sucks the big one! I thought that selecting a snapshot would automatically restore to that point in time. Not so!

Another really, really annoying thing about sbackup is... when I select eg /home/me to restore, it creates a random directory like "tmp82gaT" in my /home/me directory, and then creates tmp82gaT/home/me/ and extracts the files into that! WTF? 

I cannot get this program to simply restore /home/me to /home/me.

---

### Post by jokaiser on 2010-09-24
Hi, a year has passed and the problem is still around:
I have configured sbackup to do hourly incremental backups, assuming that restoring one of the backups would automatically restore the directory as it was at the time of the backup, But it only restores the increment. Bummer! Since there are MANY increments, restoring the last full backup and all the incremental ones manually is very tedious. So I tried to do this in a for loop on the command line. Unfortunately, that makes srestore.py crash, leaving loads of tmp* directories that fill up the hard disk. Does anybody know an alternative way of applying all the increments since the last full backup? Or, for the future, a better backup utility?
Cheers, Johannes

---

### Post by warfie on 2011-07-22
Still no answer to this?

---

### Post by juanmah on 2011-08-01
I had the same problem. Version 0.11.4

This makes incremental backup almost useless.

---

