---
title: "Best backup tool: rdiff-backup or rsync?"
date: 2006-07-26
forum: General Help
---

### Post by jordilin on 2006-07-26
What's the best tool to perform backups? I'm between two: rdiff-backup or rsync.

---

### Post by simonn on 2006-07-26
> **jordilin said:**
> What's the best tool to perform backups? I'm between two: rdiff-backup or rsync.

rsync just mirrors, so if you backup nightly, make a change on tuesday, make another change on wednesday and on thursday you want to revert to tuesdays backup because wednesdays changes were borked, you can't. With rdiff-backup you can.

However, it ultimately depends on what you are backing up though. If you are backing up files which do not change much e.g. photos, music and video, then rsync may be better.

I use a combination of both, rdiff-backup for nightlys of /home and rsync for media (photos, movies, mp3 etc).

---

### Post by jordilin on 2006-07-26
> **simonn said:**
> rsync just mirrors, so if you backup nightly, make a change on tuesday, make another change on wednesday and on thursday you want to revert to tuesdays backup because wednesdays changes were borked, you can't. With rdiff-backup you can.

However, it ultimately depends on what you are backing up though. If you are backing up files which do not change much e.g. photos, music and video, then rsync may be better.

I use a combination of both, rdiff-backup for nightlys of /home and rsync for media (photos, movies, mp3 etc).

I would like to do an exact copy of my /home directory to an external hard drive. I would back it up daily. So, perhaps rsync is the best solution.

---

### Post by Ozor Mox on 2007-08-10
Gigantic bump!

I'm using rsync at the moment to perform a backup to my external hard drive, and then from there to my other computer. I'm using the dry-run and update flags to protect my files against a reversal of the source and destination.

Since rdiff-backup is an actual backup solution instead of just a copying program that can be used for backing up, would I be better off using rdiff-backup?

---

### Post by jordilin on 2007-08-10
> **Ozor Mox said:**
> Gigantic bump!

I'm using rsync at the moment to perform a backup to my external hard drive, and then from there to my other computer. I'm using the dry-run and update flags to protect my files against a reversal of the source and destination.

Since rdiff-backup is an actual backup solution instead of just a copying program that can be used for backing up, would I be better off using rdiff-backup?

After some experience (this thread is one year old) I would recommend going for rdiff-backup. It does a great job. 

:guitar:

---

### Post by Ozor Mox on 2007-08-10
Hi, the thread is so old I'm surprised to see the OP replying! I've done a little experimentation and found out that rdiff-backup works brilliantly for backing up to an external device. You cannot however, then do an rdiff-backup from the backup to a third device as I have been doing with rsync to keep things extra safe. It fails because of the special rdiff directory in the first backup.

However, it is safer than rsync, as I still concern myself with running the wrong scripts and getting all the file additions and deletions in reverse. So I'm now trying to decide if one backup on my external drive is enough and to use rdiff-backup instead of rsync with two backups.

Pretty unlikely my computer would fail (or I'd mess it up!) at the same time as my external device...but then I'm paranoid :)

---

### Post by jordilin on 2007-08-11
I use rdiff-backup for incremental backups every day and once a month I make a whole backup by using partimage or mondo. There are several possibilities. Just a question of tastes.

---

