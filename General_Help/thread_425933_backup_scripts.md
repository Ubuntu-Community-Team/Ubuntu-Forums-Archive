---
title: "backup scripts"
date: 2007-04-28
forum: General Help
---

### Post by dead_end on 2007-04-28
Hey,
      Does anyone know of a better way to go about this. I was planning on dropping it in the weekly cron folder. Thanks

```
#!/bin/sh

# This is a backup script
#
# You must be root to use this. That way you don't accedentaly delete your backup files.
# I suggest that you have the save directory on another drive or at the very least on a separete partition.



#this section will rotate the backed up tar files

mv /mnt/backups/userlandfile-backup.tar.4 /mnt/backups/userlandfile-backup.tar.5
mv /mnt/backups/userlandfile-backup.tar.3 /mnt/backups/userlandfile-backup.tar.4
mv /mnt/backups/userlandfile-backup.tar.2 /mnt/backups/userlandfile-backup.tar.3
mv /mnt/backups/userlandfile-backup.tar.1 /mnt/backups/userlandfile-backup.tar.2
mv /mnt/backups/userlandfile-backup.tar  /mnt/backups/userlandfile-backup.tar.1
rm /mnt/backups/userlandfile-backup.tar.5

#this section will create a tarball of the home directory.
tar -cvf /mnt/backups/userlandfile-backup.tar /home

exit
```

---

### Post by kidders on 2007-04-29
Hi there,

I'm not altogether sure, but perhaps you're wondering about other ways of writing the sequence of **mv** commands? One alternative would be something like...

```
#!/bin/bash

DIRNAME='/path/to/archives'

for i in $DIRNAME/*.[0-9]; do
        NUM=`echo $i | sed 's/.*\.//'`
        echo mv $i $DIRNAME/$(basename $i .$NUM).$[$NUM+1]
done
```

...ie something involving a loop of some sort.

In general terms, since this script will be repeatedly executed without notice, you should try to think of things that might go wrong, and what effect (if any) they might have, over multiple executions. For instance:

[LIST]
[*]Could one of the files being renamed (or deleted) be open at the time?
[*]Are the files large enough to cause any disk space concerns?
[*]Would it be disastrous (or just inconvenient) if _one_ of the **mv** commands were to fail for some reason?
[*]Etc, etc...[/LIST]Also, **tar -cvf** should really be replaced with **tar cf**, imo...
[LIST]
[*]The '-' character is not required.
[*]The 'v' will generate output.
[*]If you wanted to, you could compress your archives, with **tar czf...** or **tar cjf...** although these would take longer (and use more CPU) to execute.[/LIST]Usually, cron tasks should be designed *not* to produce any output, unless something has gone wrong. Typically, the system running the task then mails a predefined user the output, as a warning that something's not quite right.

Is any of this helpful?

---

### Post by dead_end on 2007-05-04
I think so. I'll try your suggestions and see how it works. I had set it up for multiple backups on the chance that one of the backups was faulty.  Space is not to much of a problem as the home dir is a 30 GB partition and the backup drive has a single 160 GB partition.  If I was to change the backup files' permissions  so that only root can operate on them that would help to ensure that the files are not open when it is being run.  If one of the mv commands were to fail would it keep the script from creating the new backup file? If so how would I work around that?

---

### Post by kidders on 2007-05-05
Hey again,

> **dead_end said:**
> If one of the mv commands were to fail would it keep the script from creating the new backup file?Probably not. What I was referring to was this sort of thing...[LIST=1]
[*]Move backup #4 -> #5
[*]Move backup #3 -> #4 [COLOR=Red][**Fails**][/COLOR]
[*]Move backup #2 -> #3
[*]Move backup #1 -> #2
[*]Drop backup #5
[*]Recreate backup #1[/LIST]The result would be the loss of backup #3. If that would be irrelevant, then there's no problem; if it would be bad, then you would need to kill the script. Something like that isn't very likely to happen, but I wanted to draw attention to peculiar failures, just in case you hadn't considered them.

One other possible idea would be to use the output of something like **who -q** to decide whether to do the backup. That would avoid issues arising from source files being modified during the backup, and put off all the I/O (which would cause performance lag) until no-one was using your box. (It could be quite annoying if you were busy playing doom3, when your machine suddenly decided to copy 30GB of data around your disks!) You could...[LIST]
[*]Schedule a backup once every 30 mins, from 3am to 5am.
[*]Depending on the modification date of userlandfile-backup.tar, the backup script would quit, without doing anything.
[*]If it was 5am (ie there would be no further opportunity to perform the backup), the script would continue, regardless of who was logged in.
[*]Otherwise, the script would only do the backup if nobody was using the PC.[/LIST]Just a thought.

The main reason for making suggestions like these is that there are plenty of reasonably good backup programs already in existence. The only advantage you get from scripting the process yourself is the ability to customise the backup a little.

---

### Post by pete.dawgg on 2007-11-16
it's cool to do everything with self-written shellscripts, but in ur case u might be better off with **rsnapshot** (you can install it with apt).
it's fast (uses rsync), flexible, you can run it with cron or by hand or with a shutdown-script or ...); you can have hourly, daily, weekly, mothly intervals etc. and it works thru ssh for network backups.

---

