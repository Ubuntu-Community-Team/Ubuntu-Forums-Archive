---
title: "Can't do backup"
date: 2007-08-08
forum: General Help
---

### Post by x1a4 on 2007-08-08
Hi,

How do I diagnose & correct this behaviour?  Thank you. 


# sbackupd &
[1] 22914
I: Securing target directory at: [ftp://user:pass@ftpserver.com/storage/backup](ftp://user:pass@ftpserver.com/storage/backup)
I: Securing permissions at: [ftp://user:pass@ftpserver.com/storage/backup/2007-06-17_16.14.59.273823.wendy.ful](ftp://user:pass@ftpserver.com/storage/backup/2007-06-17_16.14.59.273823.wendy.ful)
Traceback (most recent call last):
  File "/usr/sbin/sbackupd", line 404, in <module>
    upgrader.upgrade_target( target, purge )
  File "/usr/sbin/upgrade_backups.py", line 60, in upgrade_target
    self.upgrade_tdir( target+"/"+adir )
  File "/usr/sbin/upgrade_backups.py", line 78, in upgrade_tdir
    v = self.openfile( tdir + "/ver" )
  File "/usr/sbin/upgrade_backups.py", line 307, in openfile
    return gnomevfs.open( uri, 1 )
gnomevfs.NotFoundError: File not found

[1]    Exit 1                        sbackupd
#

---

### Post by nitro_n2o on 2007-08-08
can you provide more info?? 
Is this the first time that happens? are used on backing up data and it suddenly broke today? 
what is that program u r using? how did you install it?

---

### Post by ruibernardo on 2007-08-09
It seems you didn't configure sbackup. Run the GUI from the menu to do it. Sbackup only runs with a valid configuration file. If you don't have X installed, you still can configure it, by editing with a text editor like nano:

```
sudo nano /etc/sbackup.conf
```

---

### Post by x1a4 on 2007-08-09
Up until now I used the Simple Backup GUI to do manual backups.  Each time it told me the backup was started in the background and showed me the pid.  When I would ftp the server I saw the backup directories and assumed all was well, until a couple of days ago when I wanted to roll back some files and noticed the backup directories were all empty, so I ran sbackupd manually and got the error.  I reinstalled simple backup just to be sure and the same error comes up.  

I configured simple backup using the GUI and double checked sbackup.conf manually to ensure it was configured properly, and it is.  

I have all the gnomevfs packages installed except for ntfs support and ruby bindings.  

Clearly the scripts can't find a file but the error doesn't tell me which one.  Might this be a Python dependency issue?

---

### Post by ruibernardo on 2007-08-09
Can you see if this bug applies to your case?

[https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/67814](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/67814)

---

