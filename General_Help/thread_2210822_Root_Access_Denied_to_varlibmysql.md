---
title: "Root Access Denied to /var/lib/mysql"
date: 2014-03-12
forum: General Help
---

### Post by spock3 on 2014-03-12
Successfully installed MySql 5.5 from the command line, conducted all normal database operations using both
Navicat 11.16 & Mysql Workbench.

TI then Needed to access the data directory, but getting denied.


```

~$ cd /var/lib/mysql
bash: cd: /var/lib/mysql: Permission denied

```

Using Navicat, I updated the server privs to all on my root account.

But thinking the file directory access is Ubuntu 12.04 related.

How can I resolve (newbie to Linux, but have experience back to DOS 2.1)

Thanks

---

### Post by steeldriver on 2014-03-12
What do you mean exactly by your "root account"? An account that belongs to the 'sudo' group may elevate to root privileges by preceding commands by 'sudo', but is not a "root account".

```

$ ls -ld /var/lib/mysql/
drwx------ 6 mysql mysql 4096 Mar  5 17:48 /var/lib/mysql/
$ 
$ ls /var/lib/mysql/
ls: cannot open directory /var/lib/mysql/: Permission denied
$ 
$ sudo ls /var/lib/mysql/
[sudo] password for steeldriver:
debian-5.5.flag  ib_logfile0  mysql               performance_schema  test
ibdata1          ib_logfile1  mysql_upgrade_info  phpmyadmin

```

---

### Post by spock3 on 2014-03-12
Thanks, let me clarify.

The account (original admin) I use to log into my 12.04 desktop.

I recreated your code results provided above exactly, but am not able to retrieve
the contents of the terminal session, even though it shows in my switcher list.

---

### Post by steeldriver on 2014-03-12
Sorry I'm not familiar with a "switcher list"

What exactly are you trying to do (in the bigger picture...)?

---

### Post by spock3 on 2014-03-12
I need to locate the file directory containing the actual MySql database so as to setup a LibreOffice connection to query the same database.

Sorry for the incorrect syntax, the "switcher list" reference is the list of open applications one gets when you "alt+tab" within the desktop gui.

---

### Post by steeldriver on 2014-03-12
Hmm... you wouldn't normally need to access the raw database *files *in order to set up a database connection - are you following some kind of instructions / tutorial that is telling you otherwise? Usually it would be a matter of setting up a connection to the running server/port via a database driver (ODBC/JDBC/etc.)

---

### Post by spock3 on 2014-03-12
Yes, was following [this tutorial]("http://enduserguides.com/software/office/libreoffice/libreoffice_base/eug_create-a-db-connection-in-libreoffice-base.html") for a direct MySql connection.

But, that aside, to gain access to see the directory contents without using Sudo, do I need to change that directory folder
permissions to me as owner with r/w privs?

---

### Post by SeijiSensei on 2014-03-13
First, you don't need access to /var/lib/mysql to access the database from LibreOffice.  Make sure the server is listening on its network port and connect to that. If LO is running on the same machine as MySQL, use "localhost" for the server name. You'll also need an ODBC or JDBC driver on the client.

Second, the owner and group for /var/lib/mysql is the "user" mysql in group mysql.  The MySQL server daemon runs as the mysql user and can thus access the databases.  There are good reasons why this arrangement exists, and you should leave it alone.  Figure out how to access the server over the network. 

I use PostgreSQL pretty much exclusively and run MySQL only when applications demand it.  LibreOffice includes its own PostgreSQL driver (packaged as libreoffice-sdbc-postgresql on Ubuntu) so I can avoid the ODBC/JDBC issues entirely.

---

### Post by spock3 on 2014-03-13
Thanks, SeijiSensi.

I'll re-approach LO with the suggested config settings.

Will advise only as needed.

Cheers

---

