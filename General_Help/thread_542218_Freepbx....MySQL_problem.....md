---
title: "Freepbx....MySQL problem...."
date: 2007-09-03
forum: General Help
---

### Post by rayj00 on 2007-09-03
I'm trying to install FreePBX on Ubuntu 6.10 Edgy.
Asterisk is installed, MySQL is installed.
Now I am trying to do this:

Set up MySQL for use by FreePBX

Before you can do anything to MySQL, you need to make sure it's running:

root@server:~# /etc/init.d/mysql start 
Starting MySQL database server: mysqld.
root@server:~#

Now, to configure the databases for FreePBX:

root@server:/usr/src/freepbx# mysqladmin create asterisk 
root@server:/usr/src/freepbx# mysqladmin create asteriskcdrdb
[B]root@server:/usr/src/freepbx# mysql asterisk < SQL/newinstall.sql
root@server:/usr/src/freepbx# mysql asteriskcdrdb < SQL/cdr_mysql_table.sql 
[/B]

The bolded MySQL statements above are failing with:

-su: SQL/newinstall.sql: No such file or  directory

and 

-su: SQL/cdr_mysql_table.sql: No such file or directory

Any ideas?

Thanks,

Ray

---

### Post by hoevens on 2007-11-25
I saw your question and I have exactly the same problem.

I think that you need to get it as described in the manual as :

root@server:/home/user:# cd /usr/src/ 
root@server:/usr/src# svn co [https://svn.sourceforge.net/svnroot/amportal/freepbx/branches/2.1](https://svn.sourceforge.net/svnroot/amportal/freepbx/branches/2.1) freepbx

I guess it comes along with those commands BUT

apparantly I cannot resolve "svn.sourceforge.net" allthough I am connected to the internet. 

Did you found a solution yet for the problem?

Best regards,

Stefaan

---

### Post by mployee8 on 2008-02-20
I'm having the same problem with configuring Mysql. As far as the svn repository it no longer exists. It can be found at [http://svn.freepbx.org](http://svn.freepbx.org)

---

