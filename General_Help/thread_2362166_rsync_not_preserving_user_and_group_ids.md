---
title: "rsync not preserving user and group ids"
date: 2017-05-25
forum: General Help
---

### Post by jzambon on 2017-05-25
I have a new cluster and I'm trying to back up the downstream nodes.  I have an rsync script that runs on server A to remotely retrieve files from server B and save on server A.  I have figured out how to sudo into server B to get all of the files.  The trouble is, that after running rsync (yes, I waited until it finished) all of the files are saved as the username that ran the script on server A rather than the original user:group IDs on server B.  My concern is that if I need to restore from backup, that the user:group permissions will cause issues.

```

rsync -azxv \
--exclude= [a bunch of excluded directories] \
--rsync-path="sudo /usr/bin/rsync" --numeric-ids USER@node"$node_id":/ $backup_drive/backup-$date >> $backup_drive/logs/backup-$date

```

I also added rsync under my username in visudo to run sudo rsync remotely (on server B)...

```


USER ALL= NOPASSWD:/usr/bin/rsync

```

What else am I missing?  Thanks!

---

### Post by TheFu on 2017-05-25
You have to use root on both sides of the connection to 'get' all the files and 'put' all the files.

---

### Post by jzambon on 2017-05-25
SOLVED.  I was having trouble with this... connecting to server B from server A required a password.  It shouldn't since we're using ssh keys.  I found [this thread]("https://ubuntuforums.org/showthread.php?t=2065850") and specified the ssh keys in my rsync command...

```

sudo rsync -azxv \
--exclude= [a bunch of excludes] \
**-e 'ssh -i /mnt/home/USER/.ssh/id_rsa'** --rsync-path="sudo /usr/bin/rsync" --numeric-ids USER@node"$node_id":/ $backup_drive/backup-$date >> $backup_drive/logs/backup-$date

```

Thanks!

---

### Post by TheFu on 2017-05-25
you shouldn't need to specify -e anything.

ssh has been the default for rsync for over 15 yrs now. Certainly all older distros have caught up with that.The --rsync-path shouldn't be needed either, but if you must use sudo on the remote system, that is probably the only way.  I would have created ssh-keys for the local root, pushed the public key to the remote root account and runs the rsync command as 
```
# rsync -avz  --exclude="" --numeric-ids --progress --stats root@node:/ /backups/$node/
```

If I were trying to do versioned backups, I wouldn't use rsync. I'd use rdiff-backup.  The command looks very similar.
```
# rdiff-backup --exclude="/"  --include="everything I really want"  --exclude-special-files  root@node:/ /backups/$node/
```
The include/exclude stuff works about the same.  The first run is like an rsync, but every run after that is like a diff - very fast.  No funny file formats.  permissions, users, groups, acls are stored outside the files themselves, so changes like that are also part of the versioning which rsync loses over time.  The most recent backup looks like a mirror (rsync), it is only the older backups which have gz'ed diffs. Having 60-120 days of versioned backups is a great thing.  Space wise, 1.10-1.30x the size of the original depending on how much change actually happens. It is a mirror, so it will always be larger than the original.

Kirya.net has a good [rdiff-backup tutorial]("https://www.kirya.net/articles/backups-using-rdiff-backup/"). Google finds it easily.  Oh ... and since it is based on librsync, ssh is the default tunnel method used and ssh-keys work as you expect. Fully supported as is the ~/.ssh/config file so no need to remember userids, ports, IPs, all that extra stuff - like you can only allow rdiff-backup as the single command for remote root on the box. Or setup a "backup-specific" username with a UID=0 just for backups and limit it.  Very handy and it keeps the ssh-keys out of root, only in the "backup-specific" username HOME.

But ... there are 50 other methods too.

I use rdiff-backup and have for a very long time.  I've restored using it a few times too.  If there is a failure, it fails loudly.  Usually out of space is the failures I've seen.  Across my 15 systems, the average backup time is 2-3 minutes.  Of course, some take longer - 5-8 min and one takes an hour, but that is due to the amount of daily change data. For example, the family nextcloud system backup last night:
```
=== Time for Backups to nextcloud === 
StartTime 1495695011.00 (Thu May 25 02:50:11 2017)
EndTime 1495695128.65 (Thu May 25 02:52:08 2017)
ElapsedTime 117.65 (1 minute 57.65 seconds)
TotalDestinationSizeChange 11823200 (11.3 MB)

```

Out of all the different backup tools I've tried and used over the decades, this has been the least hassle AND it actually works. It really is amazing how many don't work.

Regardless, happy you found an answer.

---

### Post by oldrocker99 on 2017-05-25
It's good etiquette to mark your whole thread as [SOLVED] to help others find a solution.

FWIW, I use grsymc, which works very well for me.

---

