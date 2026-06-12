---
title: "MySQL Administrator"
date: 2007-06-07
forum: General Help
---

### Post by jenkins_t on 2007-06-07
I am using MySQL Administrator GUI downloaded from Synaptic. I have a default fiesty ubuntu install. When I use Mysql admin and login to our webhost sql account and try to do a backup of of our database, I get an "Error During Backup" SQL ERROR. It doesn't give any other info. 

I have mysql admin on my XP laptop and I can do a backup there, it is on same LAN. I checked backup settings <> xp and ubuntu and both are same. 

Any ideas?

---

### Post by sfgeorge on 2007-08-18
You're not crazy... I'm having the same problem, and am using fiesty.  At first, I hoped that running the GUI as root would fix the problem: > gksudo /usr/bin/mysql-admin...but had the same problem, which was:
> **Error during backup**
SQL Error

As an alternative, I went *old school* and busted out mysqldump to do my backup: > mysqldump -h localhost -u root -p --add-drop-table --complete-insert --routines **my_database_name** > **my_backup_file.sql**

As an aside, I find it strange that my mysql.err and mysql.log in /var/log/ are both empty.  Is that the case for you as well?


Stephen

---

### Post by sfgeorge on 2007-08-19
Whoops,

It looks like my trouble (and hopefully yours) was due to a simple mistake on my part.  I've been logging into the MySQL Administrator GUI connection screen as a highly privileged user (but not root).  Logging into the MySQL GUI as your MySQL root may fix the problem.

Good luck!

Stephen

---

### Post by getmeoutofhere on 2008-03-05
Has anyone solved this problem yet?  I have a remote database, and I cannot back it up with Ubuntu - I've tried 7.04 and 7.10 (both regular and Linux Mint).  Yet backup works fine with Windows.

Error during Backup
SQL error

No error number.

---

### Post by sfgeorge on 2008-03-06
Hi there,

The thing that you'll want to check is that the MySQL login user that you are using has ALL privileges on the database(s) that you plan to back up.  If you have a "dbadmin", "dbroot" user or the like, use that as for your login credentials when you first open MySQL Administrator.

Let us know if that doesn't solve it.  Thanks.

---

