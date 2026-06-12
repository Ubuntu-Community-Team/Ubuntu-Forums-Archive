---
title: "anacron script for backup with rsync"
date: 2017-01-31
forum: General Help
---

### Post by Dave_Mann on 2017-01-31
Here is an attempt by me to set up a complete backup using anacron;  I would appreciate guidance and advice from the group.


```
#anacrontab
#
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
HOME=/root
LOGNAME=root

# These replace cron's entries
#
1    5    cron.daily    run-parts --report /etc/cron.daily
#
7    10    cron.weekly    run-parts --report /etc/cron.weekly
#
@monthly    15    cron.monthly    run-parts --report /etc/cron.monthly
#
# Use this area for future
#
#
#Backup using rsync
#
#This backs up home updating only new or changed files
#
rsync -r -t -p -o -g --progress -u -c -l -H -s /home/ /media/dave/BigStorage/Home
#
Wait to complete then start next drive
#
#This backs up Backup1 drive to Big Storage updating only new or changed files
#
rsync -r -t -p -o -g --progress -u -c -l -H -s /media/dave/backup1 /media/dave/BigStorage/Backup1
#
#Wait to complete then start next drive
#
#This backs up Backup2 drive to BigStorage updating only new or changed files
#
rsync -r -t -p -o -g --progress -u -c -l -H -s /media/dave/backup2 /media/dave/BigStorage/Backup2
#
#Wait to complete Finish job then wait 24 hours
#
#stand by while cron takes over to do this every 24 hours
```

---

### Post by ajgreeny on 2017-01-31
Who is the owner of **/media/dave/BigStorage/Home** and are you having any problems?

I assume as it is in /media that you are using an external drive?
What filesystem is on the external drive?
Please show us the output of ```
ls -la /media/dave/BigStorage/Home
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by TheFu on 2017-01-31
This isn't a "complete backup."  If that is your goal, there is much more necessary.  

Make a script with all the commands you want. Follow scripting best practices. Call that script from whatever crontab method you like.  Don't output progress - that will just fill the email summary that cron will try to email. If it cannot deliver it, then it will suck up storage in /var/ filling and filling and filling.

I wouldn't use raw-rsync for backups.  rsync is great for mirroring, but for backups, there are better choices that are based on librsync.  We all start out using rsync for backups initially. Nothing terrible about that.

Seems you only get data this way. No system settings. No list of installed packages. No server data files, like nginx, apache, mysql/mariaDB/postgress would use.  Also, you are getting lots of worthless stuff like cache files in the HOME.  What about /usr/local/ stuff and stuff placed into /root/?  I keep helpful data about the systems in /root/backup/ ... to make rebuilding things easier after a failure.  Plus, if the machine got hacked, having /var/log would be handy to figure out why. And don't forget about crontabs for the different users stored in /var/spool/.  I use cron/at for all sorts of things and wouldn't want that knowledge lost.

To make a mirror with rsync, I use
```
# /usr/bin/rsync -avz {source} {target}
```
I didn't review all the rsync options you specified.
It is possible to list multiple sources on the same rsync cmd.
rsync doesn't capture changes over time or changed to permissions over time. That makes is a failed backup method, IMHO.

/media/ is a mount area managed by the OS.  I would avoid using it for any non-temporary storage to prevent any possible confusion for permanent mounts. For my backup storage, I use .... wait for it ... /backups/ ;)

Rather than rsync, perhaps rdiff-backup would work?
```
# /usr/bin/rdiff-backup  --exclude-special-files --include /root /home /media/dave/backup2 /media/dave/backup1 /media/dave/BigStorage/
```
Might want an exclude list too.  Mine is pretty long to avoid getting useless stuff.

Start simple. Optimize the script over time.  [http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup](http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup) from 2009. It mostly looks like this still, but has been tuned some.

I use rsync for huge, never-changing, media files, but not for other files like email, scripts, code I write, or office documents and presentations.
Anyway, hope this helps.

**Restores**
Using my method, a restore takes 30-45 minutes and I'll have everything back except the huge media files in that time.  My desktop, all programs installed, basically like it was at 2am when the daily backup runs automatically. The restore method begins by looking at the current partitioning data (in /root/backup/) so I rebuild all the storage in the needed way for this machine.  Then I'll install the base OS with an ssh server off an ISO - nothing more during the install process. Next I restore /etc/ and /home and any other "data areas" like websites or DB files.  Then I feed a list of packages to be installed into the package manager and have it do those installs.  That gets me back up and working ... all that is left are things from /root/ and crontabs and maybe dealing with importing a sql dump because the backed-up DB file is corrupted.  Whenever I can, at least 5 times a year, I practice the restore using a virtual machine.  90% of this effort is the restore.  The backups take longer to setup, but matter least.  Having a backup that has never been tested is only "hope" - I need a plan that we know works.

If we were hacked and it took a few days or weeks to realize it, having daily, versioned, backups is the only way I know to recover from that.  Watching the changes over time due to the hack will be helpful.  Same for disk corruption.  If the source disk gets corrupted, that will show on the backup storage as changed data.  We have 90-120 days to recognize that corruption before losing anything forever.  A simple rsync mirror will overwrite the mirror area with corrupt data the 1st day.  And there are 999 other reasons by versioned backups are so important.

---

### Post by deadflowr on 2017-01-31
Good advice above.
My only comment would be comment out (#) the *Wait to complete then start next drive* here, or else you run the risk of the entire thing failing, since it'll see a non-existent command for Wait.
```
#Backup using rsync
#
#This backs up home updating only new or changed files
#
rsync -r -t -p -o -g --progress -u -c -l -H -s /home/ /media/dave/BigStorage/Home
#
Wait to complete then start next drive
#
#This backs up Backup1 drive to Big Storage updating only new or changed files
```

---

### Post by geeksmith on 2017-01-31
Use backintime -- it uses rsync and keeps snapshots with minimal storage usage. This works very well as long as you don't need extra rsync options.

I also use this script where I need to exclude mounted filesystems. Easy to modify for your use.
```
#!/bin/bash -e

date=$(date "+%Y-%m-%dT%H_%M_%S")
excl=~/.rsync/exclude
back=/media/me/backup/
home=${back}home/
root=${back}root/

do_backup() {
    src=$1
    dst=$2
    cmd=$3

    temp=${dst}incomplete-${date}
    done=${dst}backup-${date}
    curr=${dst}current

    [ -d "$dst" ] || $cmd mkdir -p "$dst"

    $cmd rsync "-acx${loud}" \
      --delete               \
      --delete-excluded      \
      --exclude-from="$excl" \
      --link-dest="$curr"    \
      "$src" "$temp"

    $cmd mv "$temp" "$done"
    $cmd rm -f "$curr"
    $cmd ln -s "$done" "$curr"
}

# gotta have a disk
if ! mountpoint -q $back; then
    echo Backup disk \[$back\] not mounted
    exit 0
fi

# check for terminal output
if [ -t 1 ]; then
    loud="P"
else
    loud="v"
fi

# back up home dir
do_backup ~ "$home"

# back up rootfs
do_backup / "$root" sudo

```

---

