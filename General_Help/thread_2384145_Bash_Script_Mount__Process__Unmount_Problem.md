---
title: "Bash Script Mount / Process / Unmount Problem"
date: 2018-02-02
forum: General Help
---

### Post by merrydown on 2018-02-02
Hi,

I am a complete bash / linux noob, so it might be a silly question:

I wrote the script below (in Ubuntu 16.04.1 LTS) that I wanted to use as a cron job to periodically backup one drive to a backup drive.  The idea is that it mounts the backup drive, checks for a file that exists on it - to check it has mounted - and if it exists, perform a backup of another drive onto it.  It then checks for old tar.gz archives and deletes any which are too old.  Only at that point do I want it to umount the backup drive.

I thought bash scripts ran entirely sequentially, but when I run the cron, the umount command at the end of the script is being triggered before the tasks above are complete.  It should take about 6 hours, but it finished abruptly after a couple of minutes with an error regarding umount reporting that the drive is busy.

Is there some kind of instruction timeout moving to the next line?  Or is there some way I don't know of to make the umount fire - only - after instructions above have completed?  Or am I doing something obviously wrong?

```
#!/bin/sh
mount /dev/sdc1 /backup
if [ -f '/backup/budriveok.txt' ]; then
nice -5 rsync -arx /var/zzz/zzz/zzz/serverBackup /backup;
nice -5 find /backup/ -type f -name '*.tar.gz' -mtime +120 -exec rm -rf {} \;
fi
umount /backup
```
Cheers for any guidance offered!

---

### Post by TheFu on 2018-02-03
Please use code tags when posting code or any commands+output.  Adv Reply or Go Advanced plus the (#) does it. Makes it easier to read for us.

You've come up with a good plan. Posting the script shows you've done some good work and helps us to help you. Just a few minor tweaks to make it better, more secure, and mostly foolproof. 

Hope you don't mind. I swapped out a few tools for 1 that does the job better, faster, and more efficiently.

```
#!/bin/bash

# Set some variables for convenience
BACK_DIR="/backup"
BACK_UUID="you need to look that up"
MOUNT="/bin/mount"
UMOUNT="/bin/umount"
BACKUP_TOOL="/usr/bin/rdiff-backup"
TEST_FILE="$BACK_DIR/budriveok.txt"
SOURCE_DIRS="/var/zzz/zzz/zzz/serverBackup"  # this really should be all the backup directories, /etc/, web server files, /home, space separated .... you get the idea.

echo "Info: Starting Backup `date`
$MOUNT UUID=$BACK_UUID "$BACK_DIR"
if [ -f "$TEST_FILE" ] ; then
   # Pre-backup stuff here ---- like dumping a DB or shutting down a webapp or creating an LVM snapshot

   echo "Info: Backing up $SOURCE_DIR  --> $BACK_DIR"
   nice -5 $BACKUP_TOOL --exclude-special-files "$SOURCE_DIRS" "$BACK_DIR"


   # Post-backup stuff here ---- restarting a webapp or deleting an LVM snapshot


   echo "Info: Removing old backups in $BACK_DIR"
   nice -5 $BACKUP_TOOL --remove-older-than 120D --force "$BACK_DIR"
else
  echo "Error: No file: $TEST_FILE found."
  exit 1
fi
$UMOUNT "$BACK_DIR"
echo "Info: Backup done. `date` "
exit 0

```

I didn't test this script. Could have errors. Run it from a shell with sudo to see that it does what you want.
rdiff-backup how-to: [https://web.archive.org/web/20160330235717/https://www.kirya.net/articles/backups-using-rdiff-backup/](https://web.archive.org/web/20160330235717/https://www.kirya.net/articles/backups-using-rdiff-backup/)  It can "PULL" backups pretty easily between servers.  Just list all the source directories using server::/directory ... and make certain the last directory in the list is the target for everything.

You really did an excellent job for someone new to scripting.  Much better than my first few attempts.

Even if you don't want to use rdiff-backup, the rest of the script shows how to do lots of things.  Single quotes and double-quote use is an important skill.  Almost always, you'll want double-quotes.

Good luck.

---

### Post by merrydown on 2018-02-03
Thanks very much for your reply and the encouragement.  Apologies for the incorrect formatting.

I will give this a shot!  Thanks very much for going to the trouble of writing it all out with a different tool. I will add a switch to select the type of old files deleted and then give it a shot.

Is there a reason why this tool would finish processing before running the umount unlike my attempt?

---

### Post by TheFu on 2018-02-03
Old files are handled with the --remove-older-than switch. You don't need to do anything more.  The reason for the --force is so that multiple backups in a single day are handled correctly.

When to umount is purely a judgment call.  Since I expect you have to bring down the services being backed up to get a clean, uncorrupted, backup.  Minimizing the down time is usually important.

rdiff-backup does incremental backups.  I haven't seen anyone do an incremental tar in about 30 yrs, so I assume the tar files will be full backups every day. That isn't very efficient.  rdiff-backup handles versioning, compression, remote "pull" backups, while leaving the last backup as a mirror of the source.  For 30 days of backup, only 1.1x the source file storage is needed.

To get a feel for rdiff-backup really works, backup /etc/, change 1 file (add a line or a space or new file to /etc/hosts), and backup /etc/ again.  Then go look at the target directory structure where the backups were written.  /etc is relatively tiny, so this test is quick. /etc always needs to be backed up on every system and it has "special files" that will cause issues for many backup tools.  And lots of files in there have different owers, groups, and specialized permissions.  Backups need to handle each of these things correctly, so it is a good test. The data alone just isn't enough.

The 'find' command in the original wasn't good, btw. 
```
nice find /backup/ -type f -name \*.tar.gz -mtime +120 -exec rm -f {} \;
```
is better. nice defaults are fine.  The wildcard should be escaped or double-quoted. The rm doesn't need -r.

Anyway, those are my thoughts. Not certain I answered the real question.

---

### Post by merrydown on 2018-02-05
Hi,

thanks for your reply.  The remove-older-than is not enough for this case as I only need the older *tar.gz files to be deleted.  The tars are fortnightly system backups that sit alongside the weekly incrementally backed up image files.

It turned out that umount had been called at the right time, I'd an erorr in the code which meant it only backed up the two files in the root of the folder I was pointing at.  I added a -l (lazy) switch to the umount to make it wait until drive activity had stopped before unmounting.

I have it all working now, thanks :)

---

