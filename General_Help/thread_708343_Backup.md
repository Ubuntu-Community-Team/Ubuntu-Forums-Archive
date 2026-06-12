---
title: "Backup"
date: 2008-02-26
forum: General Help
---

### Post by Ringworld on 2008-02-26
Hi,
   Can anyone advise on the best way to backup Ubuntu 7.10 along with its LAMP installation. I have MYSQL data and Postfix email data to be included in the backup.



Thanks.

---

### Post by soldats on 2008-02-26
if you have a big enough cd or flash drive just copy the whole home directory. sure it will back up a lot of non sensical stuff but it should backup mysql and all the personal data you need. if you want to only back up some stuff create a folder called backup, and anything you want to backup put inside another folder with the correct location of where it used to be. then compress it and save to flash or cd

---

### Post by azadpanchi on 2008-02-26
> **Ringworld said:**
> Hi,
   Can anyone advise on the best way to backup Ubuntu 7.10 along with its LAMP installation. I have MYSQL data and Postfix email data to be included in the backup.



Thanks.

About mysql, find out where it is being saved, I recommend using mysqldump to back up mysql data.

Also familiarize yourself with rsync, it is very useful for backups.  Many graphical GUI backup solutions use rsync in the background.
[http://www.samba.org/rsync/](http://www.samba.org/rsync/)

---

### Post by UK-Wobbie on 2008-02-26
> **Ringworld said:**
> Hi,
   Can anyone advise on the best way to backup Ubuntu 7.10 along with its LAMP installation. I have MYSQL data and Postfix email data to be included in the backup.



Thanks.

If you like to backup everthing like the full system get your self Remastersys!
[http://www.remastersys.klikit.org](http://www.remastersys.klikit.org)
It will make a full system backup of your Ubuntu computer and make a ISO image for a Live CD. :)

---

