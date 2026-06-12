---
title: "Looking for Backup tool recommendations?"
date: 2007-06-14
forum: General Help
---

### Post by Neilor on 2007-06-14
Hi folks,

I've been looking into the various backup tools and scripts for backing my desktop... usual stuff couple of home files, digital photos etc... at the moment since I've only one PC in the network I'm using a second drive and was planning to archive a full backup from the drive to DVD once a month or so.

My wish list is as follows...

- Reliable, particularly about handling open files.
- Incremental backup with cleanup (second drive is only 8x the home directory size)
- Cron/scheduling capability
- Easy restore
- Some form of notification such as tray icon of backup underway or failure... e-mail would work to.
- GUI would be preferable

Like I said I've checked out two or three apps including Sbackup & Areca, and a couple of scripts I found through google BUT... since I'm still pretty new to Linux I was wondering what's out there that meets most of my requirements.

Thanks in advance.

Neilor.

---

### Post by jasonlfunk on 2007-06-14
If you want to take a little time to learn to do some scripting, use rsync. It's very powerful and reliable.

[http://samba.anu.edu.au/ftp/rsync/rsync.html](http://samba.anu.edu.au/ftp/rsync/rsync.html)

---

### Post by Neilor on 2007-06-14
Thanks for the tip... I have been trying some rsync based scripts... the only problem I tend to run into is the notification of activity (if running as a background process).... but have to agree with you a very useful and powerful tool.

---

### Post by gerscht on 2007-06-14
I am using rsnapshot which is a wrapper for rsync (get it via synaptic) and I think it's brilliant. The use of hard links makes the disk usage very little (only changed/new files will use space), so your backup capacity shouldn't be a problem.Photos are not changing that often ;) you most likely just want to store them (like me)
After installation, take a look at the self explanatory /etc/rsnapshot.conf

---

### Post by ruffneck on 2007-06-27
I use and am very happy with Simple Backup or sbackup. You can find it in the universe repos.

---

### Post by Qu4k3R on 2007-06-28
Yep.
I am using sbackupd also.

---

### Post by venik212 on 2007-06-28
Backup seemed to be working fine, but RESTORE is useless, which makes the whole thing useless.  I tried to restore some stuff, and Simple Restore went into outer space, with no feedback on what is was doing (or not).

---

### Post by Chris Lappe on 2007-06-28
I was searching this morning for backup software and found this thread.  I tried sbackup after seeing it recommended here and it was very easy to setup and worked fine from the first run!

You folks have no idea how much this forum has helped me in the short time since I installed Ubuntu! :D

---

