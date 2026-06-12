---
title: "Webmin - Filesystem Backup"
date: 2014-09-12
forum: General Help
---

### Post by alka5eltzer on 2014-09-12
Hi all,

Be gentle with me... I'm new with Webmin and Linux

I use Webmin to manage a little a file server in an office.. its a 1TB system. (2off 1TB, RAID1)
(Ubuntu Linux Server 12.04.1)

I use Filesystem Backup to backup everything to an external 1Tb Seagate External USB drive once per week (Sunday Night). This is a gzip Archive.
Going forward - I want to set the backup up maybe like the following:

Sun Night: Full System Backup
Mon Night: Incremental Backup
Tues Night: Incremental Backup
Wed Night: Incremental Backup
Thurs Night: Incremental Backup
Fri Night: Incremental Backup
Sat Night: Incremental Backup

Is there a way to have the Sunday Night Backup the Main Big file/archive size-wise then have the incremental daily backups smaller?

So - if someone accidently deletes something on a Thursday, I can go and recover the Full System Backup and the Wed Night Backup and recover their file (or Wednesdays version at least)?

Thanks :-)

---

### Post by mastablasta on 2014-09-12
what you are looking for is snapshots. one main backup and then just any changes.

I am not really sure how is this done on server (hopefully I will soon get my self a server and find out). but anyway you have various tools like backintime, luckybackup and such that will do snapshots.

why snapshots: [http://en.wikipedia.org/wiki/Snapshot_(computer_storage](http://en.wikipedia.org/wiki/Snapshot_(computer_storage)[)]("http://en.wikipedia.org/wiki/Snapshot_(computer_storage)")

---

### Post by dragonfly41 on 2014-09-12
I'm just starting to use webmin on Ubuntu 14.04 so I'm on a learning curve.

But can't you setup your backups/snapshots using Webmin > System > Scheduled Cron Jobs?

---

