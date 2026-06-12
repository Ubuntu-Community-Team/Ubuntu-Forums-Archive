---
title: "limit+samba+connections"
date: 2008-05-14
forum: General Help
---

### Post by jdm2 on 2008-05-14
I'm setting up a sever for a class room at my school. It is running ubuntu 6.06 desktop since the person is a noob to ubuntu and i'm not that good with commands ^^. I was wondering if there is a limit to the number of people that can access the machine by samba. Is there? Thanks for the help.

P.S. I'm looking for a backup solution, but I'm having trouble in that department. Any suggestions? I have SBackup aka simple backup, but it is missing the purge function for some reason. Thanks for the help.
-jdm2

---

### Post by Monicker on 2008-05-14
samba has a max connections option, which can be specified at the share level.

```
max connections = 5
```

---

### Post by jdm2 on 2008-05-14
Thanks, I just go to the samba config file and I add it to that area?

---

### Post by Monicker on 2008-05-14
Edit smb.conf and put that restriction in the section for the share which you want to limit.

For example:

```
[FileShare]
path = /files
available = yes
browsable = yes
public = yes
writable = no
max connections = 5
```

---

### Post by jdm2 on 2008-05-14
Thanks for the help.  I will try that out.

---

### Post by talz13 on 2008-05-14
> **jdm2 said:**
> P.S. I'm looking for a backup solution, but I'm having trouble in that department. Any suggestions? I have SBackup aka simple backup, but it is missing the purge function for some reason. Thanks for the help.
-jdm2

Make a nice little backup shell script that works by rsync, like this one:
```
#!/bin/sh
rsync -e 'ssh -p 22' -avzp --delete /home/shares/school <username>@<host>:/home/talz13/homeBackups/
```

This is what I use for backing up to my web hosting account.  And if there's a folder you want to exclude from your backup, just use the --exclude option like this:
```
#!/bin/sh
rsync -av --delete /home/shares/ /media/disk/backup --exclude "/video"
```

the --delete option keeps your backup directory clean by deleting files that have been deleted in the source directory.

---

### Post by jdm2 on 2008-05-14
Thanks for the advice, but I think I need to explain a little about how I want it to backup.  There is 2 hds in the computer.  The first one is the os  and the other is storage.  On the storage drive is the folders that the users will be using.  I want it to do a daily backup of those folders and put it on the first one and if the first hd starts running out of room I want it to get rid of the old files.  I want it to backup all the files.  This is because the trash doesn't work for some reason and they don't have access to the machine.  I'm trying to set it up for if they delete something by mistake the teacher can go back to the backup and restore it.  Does that make sense?  Thanks for the help.  Talz13, thanks for the advice, I will take a look at that.

---

### Post by talz13 on 2008-05-14
> **jdm2 said:**
> Thanks for the advice, but I think I need to explain a little about how I want it to backup.  There is 2 hds in the computer.  The first one is the os  and the other is storage.  On the storage drive is the folders that the users will be using.  I want it to do a daily backup of those folders and put it on the first one and if the first hd starts running out of room I want it to get rid of the old files.  I want it to backup all the files.  This is because the trash doesn't work for some reason and they don't have access to the machine.  I'm trying to set it up for if they delete something by mistake the teacher can go back to the backup and restore it.  Does that make sense?  Thanks for the help.  Talz13, thanks for the advice, I will take a look at that.

well, if you're concerned about people losing deleted files, you can just do a straight rsync backup and remove the "--delete" option.  Anything that gets backed up there will stay until you go and delete it from the backup folder.  

Also, if you do it this way, you won't have multiple backup copies taking up duplicate space.

My second example there would work for your disk to disk backups:
```
#!/bin/sh
rsync -av /folder/to/backup/from /folder/to/backup/to --exclude "/folder/you/don't/want/backed/up"
```

If you want any help with this, feel free to PM me

---

### Post by jdm2 on 2008-05-14
That sounds fine, but I have a few questions.  Is there a way to have this do it automatically and do i have to type this into the terminal or is there a script for it some where?  Thanks for the help talz13.

---

