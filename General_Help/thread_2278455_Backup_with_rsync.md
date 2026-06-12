---
title: "Backup with rsync"
date: 2015-05-16
forum: General Help
---

### Post by leunam12 on 2015-05-16
Hi, a few years ago I was trying to install a package from source and it broke my system really bad; I had to re-install and start from zero since I didn't have any backup. Since that time I always try to backup the entire system at least once a week. I have used tar in the past and now I have been using Clonezilla for a few months. More recently I learned about rsync which I started using immediately since it allows me to do incremental backups and if I just need to restore one directory or even one file in the whole system it is very easy to do. It also has the convenience that it can be scheduled to run automatically via cron.

These are the commands that I have been using and my intention with this thread is to hear the input from more advanced users; I am not an expert on Linux and I had to read several tutorials before I came up with these commands. I would like to know if the commands are correct or if there is something that needs to be changed or if they may be improved somehow.

Command to backup root partition```
sudo rsync -aAXHxvP --delete --inplace --numeric-ids --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/home/*","/lost+found"} /* /media/username/BACKUP/root_backup
```
Command to backup home partition
```
sudo rsync -aAXv --delete --exclude={".wine/dosdevices","/*/.gvfs"} /home/. /media/username/BACKUP/home_backup
```
These backups go to a special partition in my storage drive that is formatted with the ext filesystem.
Thank you, I appreciate y'all's ;) inputs

---

### Post by oldfred on 2015-05-16
I do not consider myself as advanced by any means.

I first started with this simple script.
       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

I then added mount of my backup partition as I sometimes ended up with files in / (root).
I do not backup any system files as I just plan on reinstalling. I do have a script that does 75% of the configuration. I do copy any files in system into /home that I manually edit like my grub and a few in /etc. Then my backup of /home covers those.

I also just like to run bootinfoscript to document system configuration and save that into a folder. And export a new list of installed applications to make it easy to reinstall all of them.
      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

    
I now do use a separate excludes file.
      
 Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

    
 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

      
 Discussion of issues on rsycn bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

