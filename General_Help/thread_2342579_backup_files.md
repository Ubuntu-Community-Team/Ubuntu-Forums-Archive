---
title: "backup files"
date: 2016-11-08
forum: General Help
---

### Post by ELMIT on 2016-11-08
I tried (finally) to use backup (that comes with 15.10).

A lots (750) of files have been stored into the directory I specified with names like: duplicity-full.20161105T120523Z.vol82.difftar.gpg
All of them about 50 MB 

Can you tell me more about these files?

It is specified to make a weekly backup. I guess the next weeks file will be named like: duplicity-full.20161112T120523Z.vol82.difftar.gpg

Will it allow me to restore only certain files?

---

### Post by patlkli on 2016-11-08
> **ELMIT said:**
> It is specified to make a weekly backup. I guess the next weeks file will be named like: duplicity-full.20161112T120523Z.vol82.difftar.gpg
You might want to read [this explanation]("https://wiki.gnome.org/Apps/DejaDup/HowItWorks#Deleting_Old_Backups") on the wiki page of Déjà-Dup, which is the "Backup" utility in Ubuntu.

Without knowing your exact backup settings, I can only tell you the following:
Duplicity (the tool which does the actual work) usually won't do a full backup every week.
It does an incremental backup most of the time, which will only backup files, which were changed or added after the last full backup.
When restoring a backup, Duplicity will first restore the previous full backup and will then apply the incremental backups.
To avoid a total data loss when an incremental backup is damaged, Duplicity does another full backup every N runs.
AFAIK, Deja-Dup will also always keep at least two full backups.

> **ELMIT said:**
> Will it allow me to restore only certain files?
Yes.

> **ELMIT said:**
> Can you tell me more about these files?
Duplicity splits up the backup in many small files because
1) the filesystem on the backup storage might not support files large enough to contain the whole backup
2) when restoring only certain files, Duplicity doesn't need to unpack the whole backup, but only those archives, which contain the file you want.

---

### Post by Bucky Ball on 2016-11-08
Nothing to do with your issue, but you might want to upgrade to a supported release. 15.10 is EOL, no longer supported, no updates and that includes security updates so it will become more vulnerable online. Avoid and upgrade. 

A clean install is easiest. Trying to fix issues on a dead release will not be easy, especially when it comes to downloading anything from the repositories as there aren't any for 15.10. As you are running an obsolete release there is a good chance some of the software apps are also going to be obsolete.

Just throwing that in. It may save you some time in the long run. Good luck. :)

---

### Post by ra7411 on 2016-11-08
The best backup software I've ever used in Win or Ub is Grsync. It doesn't compress, but that saves wear on the cpu and with low HD prices, maybe that's not so important.

---

### Post by deadflowr on 2016-11-08
You restore files directly in the Files file manager (aka nautilus)
Simply open a directory and right click will give you the option to restore. (might say "revert to previous version")
Then a deja-dup popup box will show and give a you the chance to choose which versioned backup you want to restore, if you have more than one backup for that particular file, or folder you want to restore.

---

