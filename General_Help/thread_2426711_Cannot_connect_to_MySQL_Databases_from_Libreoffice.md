---
title: "Cannot connect to MySQL Databases from Libreoffice"
date: 2019-09-12
forum: General Help
---

### Post by cscj01 on 2019-09-12
I am running Ubuntu 18.04 x64 and Libreoffice 6.0.7.3.  Before all my troubles, I could use MySQL(Native) and connect to any of mysql DBs with no password..  Now, I cannot connect at all. If I don't use a password, I am told password is required.  If I use a password, I am told I cannot connect.  I can use MySQL Workbench to connect without a password to all my DBs.  All my queries and scripts run as usual.  What is going on?

---

### Post by SeijiSensei on 2019-09-12
Did you add the password to the existing MySQL account that owns the database to which you need to connect?  Or did you add another account?  If the latter, did you [GRANT]("https://dev.mysql.com/doc/refman/8.0/en/grant.html") that account the required permissions to use the database?

If you connect from the command line using "mysql --user=username --password=password databasename" does that work?

I've only used LibreOffice to connect to my PostgreSQL databases and never used a password.  I haven't done that in some time though, so perhaps LO has been modified to require passwords.  (I avoid MySQL and prefer to use Microsoft Access with ODBC to talk to my Postgres databases in the rare instance when I need to do something that I cannot do easily from the command prompt with the native psql client.)

---

### Post by cscj01 on 2019-09-12
> **SeijiSensei said:**
> Did you add the password to the existing MySQL account that owns the database to which you need to connect?  Or did you add another account?  If the latter, did you [GRANT]("https://dev.mysql.com/doc/refman/8.0/en/grant.html") that account the required permissions to use the database?

If you connect from the command line using "mysql --user=username --password=password databasename" does that work?

I've only used LibreOffice to connect to my PostgreSQL databases and never used a password.  I haven't done that in some time though, so perhaps LO has been modified to require passwords.  (I avoid MySQL and prefer to use Microsoft Access with ODBC to talk to my Postgres databases in the rare instance when I need to do something that I cannot do easily from the command prompt with the native psql client.)
Does the database have the password, or do I have the password?  If I have the password, then I do not know my password.  I am entering what I "think" my password is, but LO Base or MySQL will not accept it.

I can enter mysql from the command line with no password.  I can use and access the databases with no password with MySQL Workbench.  So I am confused as to how to proceed.

If it is my password and not the database's, how can I get my own password changed to no password?  I have found many answers on how to reset root's password to null (I presume this means no password), but I have not found one that tells how to set a user's to null.

In case you are wondering, I am the only user of my computer, and I do not allow remote access, so I do not need passwords.

---

### Post by SeijiSensei on 2019-09-13
The database stores user@host and password pairs.  It has nothing to do with the password you use to log into Linux.

You should be able to set a user's password to null the same way you would do so for root.  Instead of 'root'@'localhost' you'd use 'username'@'localhost'.

Beyond that you need to read the MySQL documentation.  As I said, I avoid MySQL in all cases unless something requires it like WordPress.

I don't use passwords either.  All my connections are either over the localhost interface or remotely over an OpenVPN tunnel from my home office to my server.

---

### Post by cscj01 on 2019-09-14
There is a bug in the LO Base UI that does not alter the password required status when changing that status.  The setting is in the zip file of the .obd (you have to change the suffix for .obd to .zip, with a backup of course).  You can observe this behavior in the contents.xml file by checking the is-password-required variable.  The solution was revealed to me by this post: [https://ask.libreoffice.org/en/question/208563/cannot-access-data-from-lo-base-file-from-forms/]("https://ask.libreoffice.org/en/question/208563/cannot-access-data-from-lo-base-file-from-forms/").  I'll mark this thread as solved.

---

