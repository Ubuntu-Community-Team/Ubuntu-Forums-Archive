---
title: "Simple backup solution"
date: 2007-12-05
forum: General Help
---

### Post by vav on 2007-12-05
I must say up front that I wasnt able to dig through all the posts on backup to find out if there's something I need... so I appeal to those who know how to do this:

As would be a common need, I want to be able to backup X number of folders to an external USB hard drive. This includes a couple of subfolders in my /home, some data from other partitions on the computer drive etc... basically a set of folders.
Further, I would like subsequent backups to be incremental... i.e. if I delete a couple of files from a folder I usually backup, they should get deleted from the backup when I next backup! Same goes for added/modified files. This means Whenever I want , I can quickly save a snapshot of all my data without having to backup all the gigs every time...

I dont need compression, or restore algorithms or automated operation or a time machine... just something that will help me meet the requirement of regular system/data backup without having to put it off for later due to the time involved.
Again if this works, I'll be able to backup my Ubuntu install periodically, since it will only update the changes every time.

This is somewhat like the sync system for PDAs/smartphones I guess.
I run Gutsy
Thanks!

---

### Post by N-t-F on 2007-12-05
I have not tried it, yet, but [this]("http://www.mikerubel.org/computers/rsync_snapshots/") may help you.

---

### Post by logos34 on 2007-12-05
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

(does incremental after first full backup)

---

### Post by pebo on 2007-12-05
I recommend you try [unison]("http://packages.ubuntu.com/gutsy/net/unison") - it'is a great piece of software and should do what you want. Also install the unison-gtk interface.

---

### Post by vav on 2007-12-05
Thanks guys... all three methods are close to what I need. I'll probably start with sbackup, since that seems the most brain-dead way of doing it. unison seems very interesting though, with the possibility of modifying the data from different computers...

---

