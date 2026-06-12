---
title: "Ideal backup system"
date: 2007-09-04
forum: General Help
---

### Post by AusIV4 on 2007-09-04
I'm looking for what I would consider to be the ideal backup system. I don't know if such a thing already exists, but if so I'd like to know where to find it. If not, I'll probably write it.

It's kind of a hybrid of incremental backups and differential backups. It would allow you to recover changed or deleted files easily, and restore your system to any point without having to apply backups incrementally. It works like this.

Initially, you do a full backup, copying all files to a folder at the backup location. For example,
/var/backup/0001

For the next backup, you do an incremental backup, copying any changed files to a new folder at the backup location: /var/backup/0002. Now here's the twist from a normal incremental backup: Any files that have not changed since the previous backup get linked to the new backup folder. For example, /etc/fstab doesn't change often, so /var/backup/0001/etc/fstab gets linked to /var/backup/0002/etc/fstab.

The result is that /var/backup/0001 is a snapshot of what the system looked like when the first backup was run, /var/backup/0002 is a snapshot of what the system looked like when the incremental backup was run, but the disk space used is only equal to the full backup + changes.

If you accidentally delete a file or trash it beyond recovery, you can go to the last backup and recover it. If you've been working with a document for quite a while, and want to compare it to the version from three weeks ago, you can simply go to the backup from three weeks ago and find the file as it was at that time.

Does anyone know if such a thing exists? If not, does ext2/3 have an archive bit? This would make backing stuff up substantially easier.

---

### Post by simonn on 2007-09-04
rdiff-backup

---

### Post by wirelessmonkey on 2007-09-04
backuppc will do this via rsync, tar, samba, and others, as will AMANDA but requires a client install.

---

### Post by mocoloco on 2007-09-07
I'm very interested in this.  I'm a big fan of [Mozy]("http://mozy.com/") on Win and Mac, and would like to find or create something similar for end users to have a "set-it-and-forget-it" incremental off site backup.
Ideally I would like to find a free or inexpensive storage provider, for example [DriveHQ]("http://drivehq.com/") offers 1GB free space, or starts at $2.99/m 2 GB.  Their tools are non-Unix friendly but they offer FTP.  Anyway there are probably other storage options, but the backup software would need to:
[LIST]
[*]Make incremental backups, exactly as you've described.
[*]Compress the data.
[*]Allow for encryption of each "increment", since most likely off site option is FTP.
[*]Upload each backup set.
[*]Allow for easy download, decryption, decompression, and restoration of data on request.
[/LIST]
That last one is I think the tallest order.  I just started thinking about this yesterday actually, so I haven't looked at or tried too many options.  Mozy actually gives the solution, on [this page]("https://mozy.com/home") at the bottom where they jokingly mention alternatives they say:
> Run a cron job of rsync, gzip and mcrypt piped over ssh to your friend's server over his DSL line.

Thanks mozy guys ;).  Now I just wonder if there are existing frontend tools that do all that.  There's an app called Simple Backup and Restore (sbackup) in the repos, and It looks like it makes inrcemental snapshots (look [here]("http://sbackup.sourceforge.net/BackupFormat"), scroll down).  I wonder if it uses rsync on the backend, but haven't determined that yet.
I think the rest, zip, encrypt, transfer, there's probably no existing tool, but a shell or Perl script could take care of that.  Then as I said the biggest one is allowing selection of a snapshot to restore and reversing the process.

---

### Post by mocoloco on 2007-09-07
Stuff I forgot.  It needs to 
[LIST]
[*]allow for specifying a max backup size
[*]Calculate space selected backup will take (accounting for compression could be tricky)
[/LIST]

---

### Post by AusIV4 on 2007-09-07
rdiff-backup is almost exactly what I was looking for. Combined with [archfs]("http://code.google.com/p/archfs/"), , my needs are more than met.

---

### Post by jfbaro on 2007-10-24
For inexpensive space, have you looked at Amazon's S3?

If we had a client similar to Mozy client we could have our data being backed up to S3's Servers. (sure it user would need an account on S3 and also pay for the storage).

I'm interested in creating an open source project for this, but I don't have time to work alone on it (it would take me 5 years to get it working...lol)

By the way, is there any client which runs "automagically" on Linux which sends the data over to an S3 storage?

If anyone is interested in creating such software, let me know. I think it wouldn't be so hard to implement a basic solution.

Cheers

---

