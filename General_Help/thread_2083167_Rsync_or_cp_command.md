---
title: "Rsync or cp command"
date: 2012-11-11
forum: General Help
---

### Post by MOGuy78 on 2012-11-11
I have just installed Ubuntu Server 10.04LTS and have two 2TB hard drives that I'm using to share my video and music files.
I'm trying to make a mirror copy of directory "/server/" to directory "/backup/" along with all of their sub-directories.  I've been looking over
different web pages that I've found, and the two main options that I've come up with are the 'cp' command and the 'rsync' command.

Using the cp command:
cp -iaruv /server/ /backup/

Or using the rsync command:
rsync -aruWv /storage/ /backup/

Do these parameters look correct, and if so, Which of these two would be more what I'm looking for?

---

### Post by oldfred on 2012-11-11
I prefer rsync, but I am not sure of all the differences.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

-l: copies symlinks as symlinks
-t: preserves modification times
-D: preserves device and special files

#!/bin/bash
# backup script
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."
rsync -aruvlP /mnt/data/Documents /mnt/backup

echo "done"
exit 0

make it executable
chmod +x mybackup.sh

run it
./mybackup.sh

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

I do not backup system, but for a server that my be different. I assume I will just do a new install and restore from the data I do backup.

---

### Post by kjohri on 2012-11-12
rsync is the preferred command. The following command should be sufficient,

sudo rsync -avz /server/ /backup/

---

### Post by MOGuy78 on 2012-11-13
All right.  Rsync looks like it's what I'll need.  Thank you both for the help.

---

