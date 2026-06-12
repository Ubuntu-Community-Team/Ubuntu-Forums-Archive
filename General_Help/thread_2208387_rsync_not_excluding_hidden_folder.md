---
title: "rsync not excluding hidden folder"
date: 2014-02-28
forum: General Help
---

### Post by beckch on 2014-02-28
I want to remove the .cache folder from the backups as each use can have thousands of files that change daily. ( and obviously, when it works, apply to  some other similar folders)

Here is the line from my script which has been working for years without the exclude, it still works but the exclude has no effect

         ${rsync_prog} -av --delete --exclude '/data/home/*/.cache/' root@${HST}:/data/home ${BF}/backup/data
I have search a number of threads but not found a solution, lots of people quote the manual but it does not work for me.

I have tried single and double quotes around the exclude and also tried putting  /data/home/*/.cache/* in a txt file and using the --exclude-from option

Any ideas?

PS its on 12.04 server

---

### Post by oldfred on 2014-02-28
I have this line.

rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup

And then this file in the same location as my rsync file.
```
# mybackup_excludes.lst
# Note: Trailing SLASHES MATTER, copy form exactly!!!
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found
/home/*/.wine
home/*/.macromedia
```

References I used:
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

   Sample rsync file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)

 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

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

### Post by beckch on 2014-03-05
I solved it by putting a backslash in front of the .

[COLOR=#000000]${rsync_prog} -av --delete --exclude '/data/home/*/\.cache/' root@${HST}:/data/home ${BF}/backup/data

This works, but I am surprised this is not posted anywhere, maybe I have some odd local setting, maybe I should explore shopt when I have time?[/COLOR]

---

