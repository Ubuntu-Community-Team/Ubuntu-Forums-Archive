---
title: "Backups; info for a system backup"
date: 2008-07-08
forum: General Help
---

### Post by gimfred on 2008-07-08
After doing a tar backup, I checked what was in the bz2 file by ```
$ tar jtf /opt/backup/sys.backup.2k807wk2.bz2  > sysbak.txt

```
which just lists the files in there.

I was curious about some of the directories that were in there, and whether they needed to be in a system backup.

After checking with [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/2.2/index.html#TOC"), it would seem that except for existing, /var mostly contains variable runtime data so could be excluded from a system backup. 

My idea is to have a system backup, a home backup and a config backup. I'm trying to work out what is essential and what is superfluous.

Does anyone know what is required for a generic, base system to work?

I'm not looking for the "backup everything" ideology, but what files are dynamically created thus not required.

---

### Post by HalPomeranz on 2008-07-08
It really depends on what your strategy is for restoring your system in the event of a catastrophic failure.  If you plan on reinstalling the OS from scratch, then all you need to do is back up user-created data.  This tends to live in places like /home, /var/mail, and sometimes in application-specific areas like /var/lib/mysql and /var/www.

On the other hand if you plan to use your backups for "bare metal" recovery, then your backups need to be a complete image of the system.  The advantage to this sort of recovery is it should get you right back to the exact state of the system as of the time of your backup.

---

### Post by gimfred on 2008-12-27
Thanks HalPomeranz, I´m just backing up user data. I am to fickle to be a solid image backup bloke. I like changing OSes

---

