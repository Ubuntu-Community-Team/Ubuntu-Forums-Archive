---
title: "msql GUI frontend"
date: 2007-09-11
forum: General Help
---

### Post by an.echte.trilingue on 2007-09-11
Hi everybody!

Does anybody know a good GUI frontend for mysql?  I need to something that will allow me to connect to a remote mysql server through an ssh tunnel.

Thank you,
-mat

---

### Post by southernman on 2007-09-11
I assume your talking about something other than phpmyadmin?

---

### Post by tvrg on 2007-09-11
[http://www.howtoforge.com/secure_mysql_connection_ssh_tunnel](http://www.howtoforge.com/secure_mysql_connection_ssh_tunnel)

---

### Post by KCPokes on 2007-09-11
Depends on what you want the GUI for?  There are essentially two packages, that aren't web-based, that come to mind.  There is MySql Query Browser (sudo apt-get install mysql-query-browser) which allows you to, as the name implies, run queries against a database (update, insert, delete).  There is also MySQL Administrator (sudo apt-get install mysql-admin) which allows you to create DBs, set up user permissions, etc...  

Personally I find phpMyAdmin and/or Webmin to be an easier solution, but the above packages are viable alternatives.

[Edit] Nevermind.  The above post is going to address the SSH requirement that I somehow completely missed.

---

### Post by an.echte.trilingue on 2007-09-11
Hey folks, thank you for the replies, but these are administration tools and I am really looking for a data-entry tool, kind of like MS Access, only for mysql and on Linux...

Any other ideas?

Thanks again,
-mat

---

### Post by KCPokes on 2007-09-11
> **an.echte.trilingue said:**
> Hey folks, thank you for the replies, but these are administration tools and I am really looking for a data-entry tool, kind of like MS Access, only for mysql and on Linux...

Any other ideas?

Thanks again,
-mat

Query Browser is essentially entry/query.  Using the same steps as detailed in the link above, with the QB application, will allow you to access it remotely.

---

### Post by tvrg on 2007-09-11
or ooo base using the ssh tunnel link

---

### Post by an.echte.trilingue on 2007-09-12
Thank you both.

Querry Browser is too technical ( I need something that somebody with no knowledge of mysql can use), oobase keeps crashing and kexi can't edit databases that it didn't create.  

Oh well.  The folks around the office who use ubuntu machines are tech-savvy enough to learn mysql and ms access is working just fine for those on windows.  

Thanks for your help.

-mat

---

### Post by resume-writer on 2007-09-14
I'd like the tools discussed here. When I run the commands to install mysql-query-browser and mysql-admin, I receive a message that says that the packages weren't found. So, I guess I need to install them. Which Linux package on [http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html) is appropriate for Ubuntu?

---

