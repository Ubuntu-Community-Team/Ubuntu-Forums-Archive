---
title: "Advice on which files should be backed up"
date: 2013-04-30
forum: General Help
---

### Post by ibates on 2013-04-30
All HDD will eventually give up the ghost (Confusius 400 BC).

To prevent much teeth gnashing and hair pulling, I believe it is a wise move to have backed up all files which might be needed and which can't be easily replaced or replicated by a new clean installation and installing available apps again.

But; which folders/files should be back up - forgetting the rubbish and data files created since the beginning?  (What to do with them is probably more an issue of emotion rather than necessity).

I would appreciate any advice on this subject. Storage space is not a problem, nor is time to backup.

---

### Post by codemaniac on 2013-04-30
few important directories to back up in a Linux file system are /etc, /home , /var . Always good to have them backed up. 

You can also take a snapshot of the installed packages every now and then.
```
dpkg --get-selections > installedPackages.dat
```

and also "The Tao of Backup". :)
 
[http://taobackup.com/](http://taobackup.com/)

---

### Post by tubbygweilo on 2013-04-30
ibates,
I would suggest that user created data ie your family photographs, your own and purchased music and I am sure you can think of many more examples should I think be your first concern as a system can always be recreated via a new install. This may help [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) I have used Deja Dup  [https://help.ubuntu.com/13.04/ubuntu-help/files.html#backup](https://help.ubuntu.com/13.04/ubuntu-help/files.html#backup) but please remember It is a good idea to verify backups and if possible store them on an external device.

ATB

---

### Post by ibates on 2013-04-30
Thank you for your advice.  It is welcomed and will be heeded.

This question is now SOLVED.

---

