---
title: "I wrote a backup script"
date: 2014-05-16
forum: General Help
---

### Post by m-dw on 2014-05-16
Hi All

It's been a long time since I've done any scripting.  I'd value your opinions on this (very simple) backup script.  I've tested it, and it does what I want which is:
[LIST]
[*]Backup files in (currently 2) directories on my raid partition.
[*]Not run if the USB storage is not attached (so I don't fill up /)
[*]Overwrite changed files without preserving earlier copies.
[*]Keep backups of deleted files
[*]Log activities to a file.
[/LIST]

```

#!/bin/bash
#
# test file
ROOT_UID=0     # Only users with $UID 0 have root privileges.
E_NOTROOT=67   # Non-root exit error.

# List folders to be backed up here
srcdirs="/raid/users
/raid/media"

if [ "$UID" -ne "$ROOT_UID" ]
then
  echo "Must be root to run this script."
  exit $E_NOTROOT
fi  


starttime="$(date -u)"
echo $starttime Backup started >> backup.log

mount -t ext4 -L backup01 /mnt/backup/
if [ $? -ne 0 ]; then
  echo "$(date -u)" Failed to mount backup disk.  Backup FAILED >> backup.log
  exit
else
  echo "$(date -u)" backup disk mounted >> backup.log
fi


for srcdir in $srcdirs
do
  stats="$(rsync -ah --info=stats2 $srcdir /mnt/backup/ | grep transferred)"
  files="$(echo $stats | awk '{ print $6 }')"
  bytes="$(echo $stats | awk '{ print $11 }')"
  echo "$(date -u)" Backup of $srcdir: $files files, $bytes bytes copied >> backup.log
done

diskfree="$(df -h --sync /mnt/backup/ | grep backup | awk '{ print $4 }')"
echo "$(date -u) All backups completed succesfully. $diskfree free on backup01" >> backup.log

sync
umount /mnt/backup 
echo "$(date -u) Backup completed, drive umounted" >> backup.log

```

Would appreciate your comments before I commit it to the root crontab.  In particular have I done anything here that could give rise to a fault that could crash the server if something doesn't work as expected?

Also am thinking of writing the backup.log to a folder on my web server so I can access it without logging in to the server directly.  Is this a bad idea?

---

### Post by TheFu on 2014-05-16
There are 1,000 different ways to the same solution.  A few ideas are below. Take what you like, ignore the crap.  It is your machine, not mine. ;)

Every command run should have a full path to prevent a change in PATH from screwing you.  mount, rsync, umount, date, df, awk all need full paths. Use environment vars set at the top to keep this simple.  Sometimes commands change and the options used change. Often the old-style command remains - like when SysV overtook BSD-style commands.

Every output file needs full paths too - backup.log should be /some/full/path/    - and I'd probably date-tag the file and keep a few around 2-10 weeks worth.  logrotate can manage this for you.  Use an environment variable for the logfile too.

I'd validate that the mount command worked by checking a file exists that would only be there if the mount happened. 1 time this fails and you'll know why.

Also, I wouldn't trust the UID environment variable without filling it in myself.

rsync is find for large media files, but not-so-good for files that change all the time and could become corrupted. A backup tool that handles verioned backups is needed.

You are missing lots of relatively small stuff in the backup that would allow a system to be restored completely relatively easy.  /etc and a list of installed packages would be a start. If you run a web server ... then /var/www might be desired.  If you ever install programs from source, then /usr/local ... stuff like that.

By default, cron will email the results of a task.  If you setup postfix as a satellite install, you can send the email anywhere you like. This is better than dropping it on a public webserver, IMHO.

BTW, I don't follow my own rules above always, but for backups, I do. It is just too important to fail.

---

### Post by m-dw on 2014-05-16
Thanks for replying so completely, I really appreciate it.

> **TheFu said:**
> Every command run should have a full path to prevent a change in PATH from screwing you.  mount, rsync, umount, date, df, awk all need full paths. Use environment vars set at the top to keep this simple.  Sometimes commands change and the options used change. Often the old-style command remains - like when SysV overtook BSD-style commands.

That's excellent advice.  I'll do some further reading (am using the Advanced Bash-Scripting Guide) and add this into the next version.  I can continue calling it manually with sudo for the moment.

> Every output file needs full paths too - backup.log should be /some/full/path/    - and I'd probably date-tag the file and keep a few around 2-10 weeks worth.  logrotate can manage this for you.  Use an environment variable for the logfile too.

Yes, definitely.  I left it relative for testing purposes. I'll set the log directory as a variable and prepend it to the file name.

> I'd validate that the mount command worked by checking a file exists that would only be there if the mount happened. 1 time this fails and you'll know why.

Is that more reliable than looking at the exit status of the mount command?  I could actually do both.  I saw a script that does something like that so I'll maybe rip that one off.  In fact that's a better idea, as if I accidentally leave the backup disk mounted the current script stops because it can't mount the backup disk.  Maybe add some more steps:
[LIST]
[*]check if disk is mounted and mount disk if not.
[*]check content of disk to make sure it's the correct one.
[/LIST]

If I put a test file under /mnt/backup on the root partition and check for it's non-existence would that be acceptable as definite proof that the disk isn't mounted?

> Also, I wouldn't trust the UID environment variable without filling it in myself.
Don't understand that one?  The script is to be run from root's cron-tab.  Doesn't that mean it will have root privileges?

> rsync is find for large media files, but not-so-good for files that change all the time and could become corrupted. A backup tool that handles verioned backups is needed.

You are missing lots of relatively small stuff in the backup that would allow a system to be restored completely relatively easy.  /etc and a list of installed packages would be a start. If you run a web server ... then /var/www might be desired.  If you ever install programs from source, then /usr/local ... stuff like that.

By default, cron will email the results of a task.  If you setup postfix as a satellite install, you can send the email anywhere you like. This is better than dropping it on a public webserver, IMHO.

Yes, this is specifically aimed at backing up user and shared data on my home server.  My intention was to add more directories in the srcdirs variable as it becomes necessary, and to use another method for backing up stuff like databases if it becomes necessary.  It's not a public web server either and can't be accessed from the Internet.

Thanks again for your input.

---

### Post by TheFu on 2014-05-16
If you are going to the effort to backup a system, why not back up everything needed to restore it?  It doesn't matter if it is on the internet or not.  Corruption can happen for many different reasons and over time. versioned backups are critical - and when modern backup tools can have 30-90 dyas of backups for 15% more storage, why wouldn't we use them?  **rdiff-backup** commands look like rsync, but do soooooo much more.  I'm certain you will become a convert.

I didn't say anything about DBs - that is different. For small, home DBs, I just shutdown the DBMS during the backup run - that will ensure DB consistency. For work DBs, I'd dump the DB to a text file and still backup the DB file AND dumped text. If anything appeared corrupted post-restore, then I'd reload the DB from the dump.

Well, if you are positive it has root priviledges, why bother checking at all?

sudo inherits your environment.  crontab only has the environment you provide. Don't expect any environment variables to be set, unless you set them inside the script - UID is an example.

I'm confused - why just set the logdirectory and not the entire file-path as a variable? I've never seen that in any professional scripts.  Testing has nothing to do with output file locations, IMHO.

---

### Post by m-dw on 2014-05-16
> **TheFu said:**
> If you are going to the effort to backup a system, why not back up everything needed to restore it?  It doesn't matter if it is on the internet or not.  Corruption can happen for many different reasons and over time. versioned backups are critical - and when modern backup tools can have 30-90 dyas of backups for 15% more storage, why wouldn't we use them?  **rdiff-backup** commands look like rsync, but do soooooo much more.  I'm certain you will become a convert.

Ah! Main reason was I couldn't find any information on using rdiff to back up to a local disk.  I looked a bit harder just now!  I have some reading to do.  The reference to the Internet was to say it isn't a public web server in respect of publishing the back up logs through it - not that I don't really care about backing it up.

> Well, if you are positive it has root priviledges, why bother checking at all?
Ah... what I meant was I don't know how to ensure the script is executes with root privileges without setting SUID, which I know is "a bad thing".  But I also know that it needs to run with root privileges so it can preserve the permissions and ownership of files that I don't own.  In other words, could you point me to some advice on setting UID inside the script in a secure manner.

> I'm confused - why just set the logdirectory and not the entire file-path as a variable? I've never seen that in any professional scripts.

I'm sorry I really didn't mean to give the impression I knew what I was doing :lolflag:

---

### Post by Vaphell on 2014-05-16
```
for srcdir in $srcdirs
do
  ...
done
```

this thing is dirty. It's bash, you have arrays for that

```
srcdirs=( "/raid/users" "/raid/media" )

for srcdir in "${srcdirs[@]}"
do
  ...
done
```


Awk is a superset of grep functionality so grep|awk combos don't make much sense when awk can do everything

```
... | [COLOR="#B22222"]grep backup | awk '{ print $4 }'[/COLOR]
... | [COLOR="#0000CD"]awk '/backup/{ print $4 }'[/COLOR]
```

---

### Post by m-dw on 2014-05-16
Awesome, thanks.  Have added these changes, but now of course I'm off on the rdiff-backup tangent.  My scripting is hampered by a very limited knowledge of the commands I'm calling.  I'd forgotten how engrossing this kind of stuff can be!

Many, many thanks to TheFu for encouraging me to look at rdiff-backup again.  I've just done a simple test, and it was trouble-free.  Next I need to script the process and plan what directories (if any) I need to exclude, and how to log the stats, although the only one I really need to worry about is free space on the destination drive.

---

### Post by TheFu on 2014-05-21
> **m-dw said:**
> Ah! Main reason was I couldn't find any information on using rdiff to back up to a local disk.  I looked a bit harder just now!  I have some reading to do.  The reference to the Internet was to say it isn't a public web server in respect of publishing the back up logs through it - not that I don't really care about backing it up.

I have a few examples on my blog - though some are script-generated and ugly, they show the final command being used to backup a real system.  **If you understand rsync, then the rdiff-backup command should look very familiar.**  Search with "jdpfu rdiff-backup" to find those articles.

> **m-dw said:**
> Ah... what I meant was I don't know how to ensure the script is executes with root privileges without setting SUID, which I know is "a bad thing".  But I also know that it needs to run with root privileges so it can preserve the permissions and ownership of files that I don't own.  In other words, could you point me to some advice on setting UID inside the script in a secure manner.

I use a "backups" account set with uid of (0) zero. It is accessed from a remote server through key-based ssh only to pull the backups that I want.  If you need to run on the local machine as root, just put the cmd into the root crontab  (sudo crontab -e).  The crontab is good if you want a command to run at a specific time, anacron is good if you need a command to run sometime during a day, week, month, ... but don't care that it is a specific time.  anacron uses /etc/cron.daily/ scripts.

Don't forget that cron doesn't provide much of an environment and the pwd isn't useful. No not assume anything.

---

