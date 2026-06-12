---
title: "Failure Transferring files over 2 Gb"
date: 2008-02-26
forum: General Help
---

### Post by bapool on 2008-02-26
I have an Ubuntu 7.04 server running my Moodle (CMS) system for our school.  Every night it dumps the sql database and data directory to another box (Windows 2000) as a backup for disaster recovery.

I am in the process of building a new server (with 7.10) and was trying to use the files to restore the system on it for testing before rollout.  It was while I was going to restore my moodledata.tar.gz file that I realized they are all exactly 2.0GB (2147483647 bytes) exactly!  BTW the file on the Ubuntu server is actually 2.1GB.  It seems to fail at exactly that size every time it tries to copy over at night.

While I haven't lost anything, my backup routine isn't really backing up squat, as the archives aren't any good.

I can't seem to find this error anywhere.  Is is inherent in Ubuntu, Linux->Windows transfers???

It happens when I do it by hand or in my cron scripting.

Any inputs would help.

Brian

---

### Post by torgrot on 2008-02-26
Typically Windows limits NFS and Samba files to 2GB.  I don't understand why, but I have run into the limitation many times.

torgrot

---

### Post by benfindlay on 2008-02-26
Just a thought if it's not samba causing the hassle,  what is the destination drive formatted as?

NTFS shouldn't have any problems and FAT32 has a max file size of 4 gig, so it's not that; but if its a tape drive backup that you are using, it could be a different file system.

The discrepancy in the file size could also be due to different formatting types and the way they handle their minimum cluster sizes if I remember correctly.

EDIT: found a link with some info: [http://www.ntfs.com/ntfs_vs_fat.htm]("http://www.ntfs.com/ntfs_vs_fat.htm")
FAT16: max size of 2 gig apparently. Could that be it?

Hope this helps!

---

### Post by torgrot on 2008-02-26
See the following link regarding samba file sizes.
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/38886](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/38886)

torgrot

---

