---
title: "Ubuntu Server backup solution"
date: 2013-09-10
forum: General Help
---

### Post by Vejovis on 2013-09-10
I'm new to the Ubuntu world and looking for some advice for a backup solution. We currently use Symantec for our windows machines but Symantec offers little support with Ubuntu 12.04 which leads me to believe there has to be another solution for a small business to enterprise level backup. 

Thanks in advance,

V

---

### Post by Kirboosy on 2013-09-10
Welcome to the forums!

There is a page on the wiki called [BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities") that might answer your questions. Hope that helps


~Caboose

---

### Post by dragonfly41 on 2013-09-10
Add luckyBackup to the list of options.

---

### Post by Vejovis on 2013-09-10
I guess what I was hoping for was a solution like that of Backup Exec where you could set backups from a remote machine through a graphical interface. Something that would work with Ubuntu but also with Windows machines. 

Any Admins using something like this?

Thanks, 
V

---

### Post by Kirboosy on 2013-09-10
Without going to indepth, what is the general setup that you have for a backup solution? (One central backup system, multiple systems that mirror backups, etc)

I believe [Bacula]("http://www.bacula.org/en/") would be something that is similar to what you are used too.

Also there is [Amanda]("http://www.amanda.org/") however I think Bacula has more features.

~Caboose

---

