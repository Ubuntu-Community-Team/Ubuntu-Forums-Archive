---
title: "I hosed my Mysql for an app. I need some help."
date: 2022-01-05
forum: General Help
---

### Post by rsteinmetz70112 on 2022-01-05
Yesterday doing some maintenance removed a bunch of obsolete config files from one of my Computers. Somehow in the course of doing that I also broke my apache2 install and my mysql. I accidently seem to have removed random files from Apache2, php and mysql. I don't know what exactly happened.

I have managed to get apache2 back up and I have I think I fixed the php application but it seems the mysql database had some files deleted including possibly the data base files. msql runs but doesn't seem to have data. I have backups but don't know what I need to restore.

---

### Post by TheFu on 2022-01-05
DB files are usually in /var/lib/ ... somewhere. Unless you put them somewhere else.  Look there for your backups.  Do you use a snapshot or sqldump method to get clean DBMS backups?

---

### Post by SeijiSensei on 2022-01-06
If you use mysqldump for backups, I'd run a second instance of MySQL on a different port, then see if you can restore the backups to it.  Usually it's something as easy as 
```
mysql -u root < /path/to/backup/file
```
but it might be more complex than that. (I usually use PostgreSQL, and only use MySQL when an application requires it, so I'm less clear on the process for MySQL.)

If that works properly, then you can either stick with this new version on a non-standard port, or run the same restoration process on the actual MySQL instance.

---

### Post by rsteinmetz70112 on 2022-01-06
I've now solved it. I was very confused for a while I didn't knwo what had actually been deleted or damaged. 

Upon further investigation several files were mysteriously deleted during my clean up, they mostly related to the php web application preventing me running it. I restored the files from backup. It turned out the actual database files were OK but the application that accesses them had an incorrect mysql password. I was able to update the mysql password and everything is now correct.

Thanks for the help.

---

