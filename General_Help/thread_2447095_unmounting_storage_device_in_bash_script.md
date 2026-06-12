---
title: "unmounting storage device in bash script"
date: 2020-07-12
forum: General Help
---

### Post by rbmorse on 2020-07-12
I'm writing a simple bash script to run rdiff-backup in background at set intervals.  When rdiff-backup finishes, the script will unmount the partition that holds the rdiff-backup target (dedicated partition on an internal hard drive, and not on the same physical device as the source files).  

Do I need to set a sleep interval here to make sure any buffered data has time to get written to the drive, or is the umount command smart enough to wait for buffers to clear before actually pulling the plug?

---

### Post by coley9225 on 2020-07-12
Hello. I have a bash script that may help. A kind ubuntu user shared this with me, and it is quite handy.

#!/bin/bash

# Create the list of manually installed packages - use apt-mark showmanual and store that output somewhere that gets included in the /media/charles/scripted_backups.  I put it into /root/backups/
apt-mark showmanual > /root/backups/apt-mark.manual
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

######
# Clean up garbage inside all the HOME directories before doing the backup.  No need for cache or trash files, for example.

# mount the backup disk as needed; best not to leave it mounted.
mount /media/charles/scripted_backups

# Ensure /media/charles/scripted_backups are by hostname, so multiple hosts can use the same backup storage
mkdir  -p /media/charles/scripted_backups/coleys-19

# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       /media/charles/scripted_backups/coleys-19

# Remove really old backup sets - say 90 days old.
/usr/bin/rdiff-backup --force --remove-older-than 90D    /media/charles/scripted_backups/coleys-19

# umount the backup disk
umount /media/charles/scripted_backups

Of coarse you will need to modify to fit your needs, storage location, etc. When you get your script working as you want it to, go into root crontab and add an entry for your script.The following link explain how to do that.
[https://www.howtogeek.com/101288/how-to-schedule-tasks-on-linux-an-introduction-to-crontab-files/](https://www.howtogeek.com/101288/how-to-schedule-tasks-on-linux-an-introduction-to-crontab-files/)

Best of luck.

---

### Post by rbmorse on 2020-07-12
Thanks.  I've pretty much got the script worked out along the lines of yours.  The question I have is really about the umount command -- does it wait for the buffers to flush or do I have to allow for that in the script? 

n.b. I'm using systemd-timer rather than a crontab to set the interval.  Simple and straightforward.

---

### Post by coley9225 on 2020-07-12
It should wait until it is totally through before unmounting backup drive, I've never had it give me any issues. You can modify the script ,. at the end of the command to remove old backups, add '&&' like so: /usr/bin/rdiff-backup --force --remove-older-than 90D    /media/charles/scripted_backups/coleys-19 &&. That tells the script to wait untill the remove command is complete before moving on to the next command, ( the umount command.) I'm not familiar with systemd-timer, but with crontab you can configure it to run at set intervals, like every 30 minutes, or run daily, mounthy, etc. Good luck.

---

### Post by aljames2 on 2020-07-12
Commands you run in a script should use their absolute path.  i.e. **/bin/mount** vs. mount   and   /bin/umount vs. umount

To find the path to a command, simply use "whereis".  **whereis mount**  or  whereis umount

Also, I've seen tips from others that use the sleep command in a script to allow a pause before moving on.  A 2 second sleep would simply be:  **sleep 2**

---

