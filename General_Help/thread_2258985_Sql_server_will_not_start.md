---
title: "Sql server will not start"
date: 2015-01-01
forum: General Help
---

### Post by richard99 on 2015-01-01
Hi all, 

I typed in the /etc/init.d/mysql start command after installing MariaDB and now it wouldn't start.

It will try to start but will constantly fail.

Starting MariaDB database server mysqld                               [fail]

Is there a way to troubleshoot this?

Thanks.

---

### Post by toddyfranz on 2015-01-01
Hi,

is there a logfile on /var/log/mysql which more information about the failt of starting the database?

Regards, Torsten

---

### Post by SeijiSensei on 2015-01-01
I don't know where Maria stores its database, but stock mysql places it in /var/lib/mysql.  That directory and any subdirectories needs to be owned the "user" that runs mysql, which on Ubuntu is user mysql.  See if you can identify the equivalent directory for Maria and make sure it is owned by the correct user.

By the way, you should be using the "service" command to start and stop daemons on recent Ubuntu builds, e.g., "service mysql start".

---

### Post by richard99 on 2015-01-01
I got this error in the error.log
```

150101 20:09:38  InnoDB: Waiting for the background threads to start
150101 20:09:39 Percona XtraDB ([http://www.percona.com](http://www.percona.com)) 5.5.40-MariaDB-36.1 started; log sequence number 1931621
150101 20:09:39 [Note] Plugin 'FEEDBACK' is disabled.
150101 20:09:39 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
150101 20:09:39 [Note] Server socket created on IP: '127.0.0.1'.
150101 20:09:39 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'host'
150101 20:09:39 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended

```
When i try to run with service mysql start, i get this.
```
root@ubuntu:/var/log/mysql# service mysql start
start: Unknown job: mysql
```

---

### Post by SeijiSensei on 2015-01-02
Did you install this from the repositories?  I just installed MariaDB onto my 14.04 system from the repos and have none of the problems you report.  Also the command "sudo service mysql start" worked as expected.

I used "sudo apt-get install mariadb*" to make sure I got all the relevant packages.

---

