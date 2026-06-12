---
title: "backup failure"
date: 2013-10-21
forum: General Help
---

### Post by TWFJR on 2013-10-21
I backed up my home directory and attempted to restore only to  be told "No backups to restore." There is a list of files identified as "duplicity-full.****************.vol*.difftar.gpg" mostly with volumes of 25MB. Backup restore does not find files to be restored. Is there any possibility to see if my files were saved to UbuntuOne and if so to recover them another way. 
backup, deja dup, ubuntuone-login

---

### Post by TheFu on 2013-10-21
Hopefully someone with real knowledge will reply, but in the meantime ....
I understand that Duplicity uses standard file formats for storage, so, in theory, if you know they way the files are packed, then you can read the MANIFEST, determine which of the 10,000 numbered files has the data you want, grab that single file, use some mix of gpg, tar, gunzip to access the data and restore without using duplicity.  OTOH, I don't know.

I've been using rdiff-backup for a few years. It doesn't encrypt backups, which is critical if you use 3rd parties for storage, but it does work well and leaves the files in a state that makes recovering 1 file or an entire directory from the most recent backup basically a copy operation.  Just wrote an new blog post about that with a non-trivial system back example.
* Non-Trivial: [http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)
* Full-Script: [http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup](http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup)

I attempted to get duplicity working a few times myself. Never seemed to work for me. I must be stupid. I always feel stupid when it doesn't work. Any backup methodology is an unknown until a restore using it has been tested. If you can't restore from a backup, what's the point?   10% of a backup process is the "backups" - 90% is the restore.

---

### Post by TWFJR on 2013-10-29
Thanks TheFu. I thought that backup was going to be simpler than copy and paste. Now I know different. In the future I will copy and paste what I want saved.

---

### Post by TheFu on 2013-10-29
> **TWFJR said:**
> Thanks TheFu. I thought that backup was going to be simpler than copy and paste. Now I know different. In the future I will copy and paste what I want saved.

Copy/paste works fine for "data", but not so much for many other items you probably want to backup too. Maintaining file permissions, ownership, groups and any special settings usually needs more. That is why using a real backup program is important.

So a very simplistic backup would be a 100G / that would be backed up to a 200G external USB drive. When connected the USB drive gets mounted as /media/Backups. Both are formated as EXT4 (or any UNIX file system) including the backup media location. The 200G will allow 3+ months of backups to be retained.  In my world, 120% gets me 60 days of backups, but YMMV.

The command would be
```
sudo rdiff-backup --exclude-special-files --exclude=/media  /  /media/Backups
```
Run that same command over daily and incremental backups will be very quick. Only the 1st one will take time. Easy-peasy.
After the first 30-120 days, you'll probably want to remove older backups to manage space. There's an rdiff-backup command for that too. I hope this makes sense and is something easily followed.  The most recent backup looks like a mirror under /media/Backups/ , so restoring 1 file is trivial.

Anyway, I hope this helps.  Sorry that I don't know much about duplicity. I had hoped that someone else would have responded by now.

---

