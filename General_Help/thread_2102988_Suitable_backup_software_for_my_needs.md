---
title: "Suitable backup software for my needs?"
date: 2013-01-08
forum: General Help
---

### Post by Ck.asdf on 2013-01-08
First, I apologize if this is the wrong area (or entire forum) to post this question, but you guys are usually quite helpful, and after hours of researching, I've still come up empty.  I have tried several different applications with no success in my efforts to find something with similar feature-set to Cobian Backup on Windows.  Applications include: rdiff-backup, Grsync, and Duplicati.

What I am looking for in a backup program:
*Take a folder and perform a full copy to the destination, whether it be a local drive or network share of some sort.  A full copy would be created every thirtieth backup.
*Verify the checksum information to be sure the copy was not corrupted.  If it was, email me with a notification of this fact, perhaps with a list of the failed file(s).
*For the next 29 subsequent backups, perform incremental backups, placing them into dated folders.  The structure would look similar to this:
/destination/2012-12-20_full_documents/  [everything]
/destination/2012-12-21_inc_documents/  [docs changed since prior backup]
/destination/2012-12-22_inc_documents/
...
/destination/2013-01-20_full_documents/  [everything again]
*The destination files would be "plain" in the sense that they are not compressed, changed in format, encrypted, etc.  In the event that I want to recover a deleted file or trashed source drive, I don't want to have to use the software to recover the data, I want to be able to use any file browser to view the contents of the backup.
*Once my preferences are set, the backup would be automated, creating new backups as desired each evening, and removing every fourth full backup (keeping the most recent three full backups and their incremental files).  Incremental files older than 6 months (or perhaps a year) should be automatically deleted.


Thanks for any assistance you can provide!

---

### Post by haqking on 2013-01-08
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Personally i use a rsync script.

Peace

---

### Post by jacrider on 2013-01-08
The link provided by the haqking is great.

Personally, I use "Back In Time" which is easy.  My destination drive is a USB harddrive.

---

### Post by Ck.asdf on 2013-01-08
Thanks guys, I'll check out the info you both gave.

---

### Post by Cheesemill on 2013-01-09
I use rsnapshot.

---

