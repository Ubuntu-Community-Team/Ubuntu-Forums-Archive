---
title: "move my mysql"
date: 2008-06-16
forum: General Help
---

### Post by rmvg on 2008-06-16
hello all i recently lost a server and setup a new ubuntu 6.06 lts LAMP server all was working well until i copied over my /var/lib/mysql directory with my old data.  now mysql will not start and i would like to recreate the ubuntu original files to get the database back up and running. I have tried unintalling and reinstalling the mysql-server 


ps here is the resulting error

e! Current system log sequence number 0 43694.
Jun 16 02:06:04 canmail mysqld[22031]: InnoDB: Your database may be corrupt or you may have copied the InnoDB
Jun 16 02:06:04 canmail mysqld[22031]: InnoDB: tablespace but not the InnoDB log files. See
Jun 16 02:06:04 canmail mysqld[22031]: [http://dev.mysql.com/doc/mysql/en/backing-up.html](http://dev.mysql.com/doc/mysql/en/backing-up.html) for more information.
Jun 16 02:06:04 canmail mysqld[22031]: 080616  2:06:04  InnoDB: Error: page 1107 log sequence number 0 18583120
Jun 16 02:06:04 canmail mysqld[22031]: InnoDB: is in the future! Current system log sequence number 0 43694.
Jun 16 02:06:04 canmail mysqld[22031]: InnoDB: Your database may be corrupt or you may have copied the InnoDB
Jun 16 02:06:04 canmail mysqld[22031]: InnoDB: tablespace but not the InnoDB log files. See
Jun 16 02:06:04 canmail mysqld[22031]: [http://dev.mysql.com/doc/mysql/en/backing-up.html](http://dev.mysql.com/doc/mysql/en/backing-up.html) for more information.
Jun 16 02:06:04 canmail mysqld[22031]: 080616  2:06:04  InnoDB: Error: page 1106 log sequence number 0 18583146
Jun 16 02:06:04 canmail mysqld[22031]: InnoDB: is in the future! Current system log sequence number 0 43694.
Jun 16 02:06:04 canmail mysqld[22031]: InnoDB: Your database may be corrupt or you may have copied the InnoDB
Jun 16 02:06:04 canmail mysqld[22031]: InnoDB: tablespace but not the InnoDB log files. See
Jun 16 02:06:04 canmail mysqld[22031]: [http://dev.mysql.com/doc/mysql/en/backing-up.html](http://dev.mysql.com/doc/mysql/en/backing-up.html) for more information.
Jun 16 02:06:04 canmail /etc/mysql/debian-start[22162]: WARNING: mysqlcheck has found corrupt tables
Jun 16 02:06:04 canmail /etc/mysql/debian-start[22162]: /usr/bin/mysqlcheck: Got error: 1045: Access denied for user 'debian-sys-maint'@'localhost' (using password: YES) when trying to connect
Jun 16 02:06:04 canmail /etc/mysql/debian-start[22162]:
Jun 16 02:06:04 canmail /etc/mysql/debian-start[22162]:  Improperly closed tables are also reported if clients are accessing
Jun 16 02:06:04 canmail /etc/mysql/debian-start[22162]:  the tables *now*. A list of current connections is below.
Jun 16 02:06:04 canmail /etc/mysql/debian-start[22162]:
Jun 16 02:06:04 canmail zimbramon[21826]: 21826:info: 2008-06-16 02:06:01, STATUS: canmail.org: antispam: Stopped

---

### Post by rmvg on 2008-06-16
bump

---

### Post by theDaveTheRave on 2009-01-28
rmvg,

I don't know if you found a solution for this or not.

But from my understanding the best route would be to use <mysqldump>

procedure would be.

Install SQL server onto new terminal

Assuming that you had a "master / slave" type setup, use the <mysqldump> command to send all the database files to a flat file called <backup.sql>

copy these files onto the new server / terminal.

Use the following command on your new server.
```

mysql --user=root --password=yourRootPassword < /pathToYour/backup.sql/file>

```
that should do the trick.

You alternatively use the select into outfile / load data infile commands to achieve the same objective.

NOTE.

you may or may not want to have the same login names for both servers, and you may or may not want to! if this is the case you will have to tell the process to <ignore-table>
Check the documentation for this as I have never used this switch in the command.

David

---

### Post by hyper_ch on 2009-01-28
copying the binary database files while mysql is running often leads to corruption. For backups you should use mysqldump instead.

---

