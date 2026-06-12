---
title: "Permissions: giving all access for a directory"
date: 2008-01-03
forum: General Help
---

### Post by vsiege on 2008-01-03
I have not yet found the answer to this.
Have a directory that every user has rwx access to - no matter who creates the files/folders in it

Basically i want a common directory/place where all users have all access, all the time to all files and folders
Is this possible? BTW this did not solve my problem > chmod -R 777 /media/second

**/media/second**  <--------I want this directory and its children to always be fully-available to all.

---

### Post by geirha on 2008-01-03
What type of filesystem is that directory on?

---

### Post by vsiege on 2008-01-04
The file system for everything is Ext3...

---

### Post by geirha on 2008-01-04
Well, if it's ext3 and it's mounted read/write, then that command should give all users access to read, write and delete whatever they want in there (which is a bad idea imo)

What's the output of these commands? 
```

ls -ld /media/second
mount | grep /media/second

```

---

### Post by bodhi.zazen on 2008-01-04
Yea, it is not so straight forward. You can try :

```
chmod g+s /media/second
```

[http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

---

### Post by vsiege on 2008-01-04
Well all the files that are stored here are just common documents and my fiel backups from my mac and windows boxes on my LAN.


> ls -ld /media/second
drwxrwxrwx 4 thisGroup 4096 2008-01-03 23:02 /media/second
> mount | grep /media/second
dev/sdb1 on /media/second type ext3 (rw)

---

### Post by geirha on 2008-01-04
I just realized I've misread your first post. Everyone gets to write files, but because of each user's umask, the files will only be writable to the user who created them. Sorry about that.

That means the users themselves need to make sure they make their files writable to all, either by changing their umask or doing a chmod. The link bodhi.zazen explains this problem.

You could change it to a fat partition, where you set the permissions for all files and directories during mounting, and all files and directories created will have those same permissions. Fat has some downsides though, so it really depends on what kind of data will be stored there and how it will be accessed.

Running a cron-job every hour or so that chmods all the files and directories might be an option as well, not a pretty way of doing it, but again, it depends on how it will be used.

---

### Post by vsiege on 2008-01-04
I will be storing:
[INDENT]1.  primarily mac-based files
2.  some windows
3. web-related files (LAMP)[/INDENT]

I am setting it up to be used as a remote file-server/backup. The machine will only be powered on when I am backing up or testing new websites on LAMP. So I dont think the cron-job would be right for this type of operation.

**Setting Group ID**, this sounds like what I am trying to achieve. 

I coulodnt get ```
chmod g+s /home/second
``` to work

Thanks for all your help so far.

---

