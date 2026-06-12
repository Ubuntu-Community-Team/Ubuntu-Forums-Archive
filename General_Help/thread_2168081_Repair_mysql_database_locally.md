---
title: "Repair mysql database locally"
date: 2013-08-16
forum: General Help
---

### Post by cathect2 on 2013-08-16
Hi,

I have a very large database (200mb) that is giving me fits. I have it locally on my computer. What I want to know if there is some software that exists that can be used on a local file to examine, repair, etc. Is there an open source project out there for this?

---

### Post by SeijiSensei on 2013-08-16
"Giving me fits" is, sadly, not very helpful.  Are you talking about the contents of /var/lib/mysql?  What kinds of "fits"?

Have you tried using mysqldump to create a plain-text backup of the database, then reinstalling MySQL and reloading the backup?

---

### Post by cathect2 on 2013-08-16
Can I do that on my local machine? All I have is the mysql file I exported from a now defunct web account.

---

### Post by SeijiSensei on 2013-08-17
If by the "mysql file" you mean a plain-text dump of the entire database, then you should be able to install MySQL on your machine and run "mysql -u root -p < /path/to/the/dumpfile", enter root's password, and recreate the database.  There may be some details I'm missing here, since I don't use MySQL (I rely on [PostgreSQL]("http://www.postgresql.org/") instead), 

If you need more help, there are [dozens of articles]("https://www.google.com/search?q=mysql+restore+sql+dump") about this process.

---

### Post by Dave_Cleverley on 2014-03-01
Backup your table (just copy your table files to somewhere else). Than execute "repair table yourtablename". Mostly table corruptions are on index files and easyly recoverable. Unexpected shutdowns or disk space problems may have results like this. 

In case first proposition didn't help you. Use repair & restore your corrupt MySQL database by **MySQL Repair Toolbox**. It is read only in nature and successful restore table corruption in MySQL database. You can download free demo version to see the preview of your corrupt database. 

[http://www.mysql.repairtoolbox.com/](http://www.mysql.repairtoolbox.com/)

---

### Post by BellyR on 2014-07-23
> **cathect2 said:**
> Hi,

I have a very large database (200mb) that is giving me fits. I have it locally on my computer. What I want to know if there is some software that exists that can be used on a local file to examine, repair, etc. Is there an open source project out there for this?

Hey folk,

I do not consider myself good at Linux Operating Systems. Still Learning, As far as your issue is concerned, I came across a SQL database Recovery Software by SysInfoTools, but that seem to be a Windows utility. Because it is really effective, you may consider contacting the developers there. Else The power of linux is not hidden, there are plenty of commercial as well as freewares available online. You just need to perform a deep search.

---

