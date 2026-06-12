---
title: "Question abourt cron job"
date: 2012-12-09
forum: General Help
---

### Post by cogset on 2012-12-09
I'm starting to schedule some simple cron jobs,stuff like backing up the Tomboy directory or my Firefox profile,however I have a doubt:what happens if the directory to be backed up is in use a the time of the scheduled job?
Is there any possibility of data corruption,what is the policy of Cron in this case? Does it delay the action until the directory is no longer in use,or is this meaningless as data can actually be accessed and copied while still in use?
Does it make a difference if the actual command is not to copy but to compress the data instead?

---

### Post by SeijiSensei on 2012-12-09
If a file changes while using tar, it will report that fact. If you're writing a script to write the tarball, make sure you send all the output to a log file like this:

```
tar cjvpf mytarball.tar.bz2 some_directory >> /var/log/mytarball 2>&1 
```

The "2>&1" sends any error output to the same file as the standard output.

If you back up with rsync, it will only copy changed files which drastically reduces the changes problems with files changing their contents on the fly.

---

### Post by cogset on 2012-12-13
Thanks,so -theoretically- there is a possibility that running a cronjob at the wrong time could result in some data corruption?
Maybe instead of a simple command to copy the data,a script that will wait for the relevant application to close before executing the backup will be more appropriate?

---

### Post by SeijiSensei on 2012-12-13
Most of the time I run backups at like 4 am.  There's usually very little happening on my machines at that time, even on servers.  I don't back up logs in real time, which are the only files being actively written at that time of day.  I let logrotate handle backups and then copy the backups it creates.

The only time I had to worry about this problem was backing up a mail server when messages could be arriving during the backup.  I solved that problem by locking the mailbox during the backup using the "lockfile" utility.  In that case the program that was delivering the mail, procmail, knew how to handle locked mailboxes and simply postponed delivery until it could get its own exclusive lock on the mailbox.

One other common situation is writing to databases.  I use the native "dump" utilites, pg_dump and mysqldump, to write database backups, and they handle the problem of locking records correctly themselves.

Are you asking this question purely theoretically, or do you have a specific application in mind?  There's not really a generic answer because, as you see, some applications are designed to handle locking while others are not.

---

### Post by cogset on 2012-12-14
Thanks again,yes I do have a specific application in mind,namely Firefox profiles which AFAIK constantly write to some databases when running (places.sqlite and sessionstore.js are the most important coming to mind) and are also quite sensitive with other applications tampering with them while in use,so I'd like to figure out whether it would be worth the risk to back up these directories with a cronjob (which will ensure I will have continuously updated backups) or the peace of mind of knowing that there won't be any risk of data corruption would be worth the boring job of manually backing them up every time I remember to do so.

---

### Post by Cheesehead on 2012-12-14
Cron has no policy at all - it merely triggers your script or application.
Your should be worried about *that* application's ability to copy without corruption.

You can use an application like rsync instead of cp in the hope if improving data transfer quality. And/or you can rotate backups so if the most recent is corrupt, the previous backup will probably still be good.

---

### Post by cogset on 2012-12-16
I see,Cron won't do any thinking on my behalf,thanks for clarifying that ;) Probably someone more in the know could use a script that either skips the cronjob if the application is running or triggers a warning,but if I have ask I'm clearly not there yet,better to stick to manual backups for now.

---

