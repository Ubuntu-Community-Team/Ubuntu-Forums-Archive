---
title: "Copy my root folder to a backup drive"
date: 2007-08-05
forum: General Help
---

### Post by ed67 on 2007-08-05
Lots of posts here about backing up stuff, but nothing that seems to do what I want.  Here's my scenario:

I have Ubuntu 7.04 installed on my laptop.  My laptop is part of my home network with my desktop pc which is running xp.  I have a second hard drive in the xp box that I use for backups.  I back up the My Documents folder to it, basically.  I have been manually copying my Ubuntu's /home folder to it but I want to automate this.

I use a program called QuickSync from Iomega on xp, which only copies changed files to the backup drive.  Anything like this for Ubuntu?  I don't want to compress the files and I don't want to backup the entire Ubuntu partition.

Thanks

---

### Post by logos34 on 2007-08-05
perhaps SimpleBackup would work:
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite?highlight=%28backup%29](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite?highlight=%28backup%29)

---

### Post by ed67 on 2007-08-05
Thanks, it's what I'm looking for I think but I have a question.  I want to back up to a samba share.  So I would use a remote directory SSH or FTP?  I copied the path to my backup drive which starts out as smb://192.168.1.2 and so on.  However, that doesn't work.

Any advice from this point?

---

