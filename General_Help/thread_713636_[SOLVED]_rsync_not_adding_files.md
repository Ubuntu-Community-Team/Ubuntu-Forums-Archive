---
title: "[SOLVED] rsync not adding files"
date: 2008-03-02
forum: General Help
---

### Post by eidauk on 2008-03-02
I do incremental backups to an external hard drive with rsync. However, I've noticed that if I run:
```
rsync -avvh --delete --progress --log-file=/home/linuxuser/Desktop/rsync_log.txt --stats --exclude=Backup --exclude=Network --exclude=.VirtualBox --exclude=.Trash --exclude=.cache /home/linuxuser /media/disk/backup
```
then add some files to the source location, then run rsync with the same code above, the files don't get updated (added) to my destination location. Isn't that what the -a option is supposed to do - update files?

---

### Post by PaulFr on 2008-03-03
I would suggest you look at the **-R** option to rsync : This will allow rsync to recurse into subdirectories under your parent directory and store it as relative directories.

If the problem persists and your timestamps are not in sync between your backup device and your system, then you may consider **-c** option, but it will slow things down, since rsync will perform a checksum rather than rely on the timestamp of the file.

---

### Post by eidauk on 2008-03-04
Thanks Paul. The -R option fixed the problem.:)

---

