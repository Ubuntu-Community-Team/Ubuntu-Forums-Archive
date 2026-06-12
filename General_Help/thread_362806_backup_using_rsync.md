---
title: "backup using rsync"
date: 2007-02-16
forum: General Help
---

### Post by antw on 2007-02-16
I am using a script with rsync to backup a drive and my home folders. The problem is that while backing up my the drive is fine, when I back up the home folders it always rewrites all the files. The statement below shows the commands and exclusions the script is using. The "u" in the script forces rsync to skip any files for which the destination file already exists and has a date later than the source file, but it is not doing this. 

Any ideas why? And what command would you use to not back up hidden folders? 

rsync -vurtp --progress --delete --exclude=.Trash/ --exclude=.icons/ --exclude=.local/ --exclude=.cedega/ --exclude=.wine/ --exclude=.thumbnails/ --exclude=.ut2004 --exclude=.picasa /home /media/usbackup

---

### Post by mannheim on 2007-02-17
What type of file system is there, for /home and for the backup drive? For example, is the backup formatted with ntfs or fat or ext2/3? Sometimes this matters, because different filesystems have different granularity for the timestamps of files, leaving rsync confused about whether the files on /home have the same modification time as the copies in the backup. If this is the problem, then the option --modifiy-window=1 (or similar) should be added to the rsync command.

---

### Post by antw on 2007-02-17
you are right back my backups are formatted differently. The one that works without a problem is formatted in FAT32, the other which I am having the problem with, is formatted in EXT3.

I tried the --modify-window=1 but it did not have an effect.

thanks for the reply

---

### Post by mannheim on 2007-02-19
> **antw said:**
>  the other which I am having the problem with, is formatted in EXT3.


So you are backing up files from a drive formatted as ext3? If so, what file system is on the destination -- where the files are backed up?

As well as the timestamp problem, there may be a problem with the -p option that you are using. This means "preserve permissions". If the destination is FAT, then it won't support permissions, and every time rsync checks, it will see different permissions on source and destination. This may cause it to copy the files again.

---

### Post by antw on 2007-02-24
I have found and tried "pybackpack" in the repo's. It has a nice simple gui and is easy to setup.

Again with this program it fails when trying to backup my home folders but unfortunately does not say why except for file security problem. My other folder that I backup works fine as it does using rsync.

So I will investigate further into the permissions of my home folder files. Are there any hints or programs that may help me in finding the problem?

---

