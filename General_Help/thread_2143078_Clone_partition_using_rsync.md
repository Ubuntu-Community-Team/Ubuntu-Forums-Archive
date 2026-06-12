---
title: "Clone partition using rsync"
date: 2013-05-07
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-05-07
On my laptop i intend to make a small partition on my hdd to backup my ssd to in case something happens during firmware updates
so i want rsync to copy links as links and not follow them
don't follow file system mounts (eg /home and /media)
preserve file permissions and ownership

---

### Post by oldfred on 2013-05-07
I include this as part of my rsync script so I know what I am doing.

```
#!/bin/bash
# backup script - mybackup.sh
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks
# -i, --itemize-changes
# -t, --times preserve modification times
# --exclude option to prevent copying things

```

I started simple like this one:
       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

Then I added an extract of installed files with dpkg, and a new run of bootinfoscript and some other system documentation files just to have them. The I found most of my copy was a lot of temporary files or cache and added an excludes file.
      
 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

I do not do this as I manually copy any file I manually edit into another folder in /home for backup.

 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)


 Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)
      
 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

