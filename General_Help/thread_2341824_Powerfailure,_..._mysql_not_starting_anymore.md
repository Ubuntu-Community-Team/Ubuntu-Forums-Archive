---
title: "Powerfailure, ... mysql not starting anymore"
date: 2016-11-01
forum: General Help
---

### Post by ELMIT on 2016-11-01
I got a UPS, but the construction work of lasted hours longer than my UPS can hold.

After restarting the computer, mysql did not start.

I tried: 
```
service mysql status
&#9679; mysql.service - LSB: Start and stop the mysql database server daemon
   Loaded: loaded (/etc/init.d/mysql)
   Active: failed (Result: exit-code) since &#20108; 2016-11-01 12:15:01 CST; 12min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 4117 ExecStart=/etc/init.d/mysql start (code=exited, status=1/FAILURE)

11&#26376; 01 12:14:31 ronald-desktop mysqld[4299]: InnoDB: then you can remove the .ibd file, and InnoDB will do a normal
11&#26376; 01 12:14:31 ronald-desktop mysqld[4299]: InnoDB: crash recovery and ignore that table.
11&#26376; 01 12:14:31 ronald-desktop mysqld[4299]: InnoDB: 3) If the file system or the disk is broken, and you cannot remove
11&#26376; 01 12:14:31 ronald-desktop mysqld[4299]: InnoDB: the .ibd file, you can set innodb_force_recovery > 0 in my.cnf
11&#26376; 01 12:14:31 ronald-desktop mysqld[4299]: InnoDB: and force InnoDB to continue crash recovery here.
11&#26376; 01 12:15:01 ronald-desktop mysql[4117]: ...fail!
11&#26376; 01 12:15:01 ronald-desktop systemd[1]: mysql.service: Control process exited, code=exited status=1
11&#26376; 01 12:15:01 ronald-desktop systemd[1]: Failed to start LSB: Start and stop the mysql database server daemon.
11&#26376; 01 12:15:01 ronald-desktop systemd[1]: mysql.service: Unit entered failed state.
11&#26376; 01 12:15:01 ronald-desktop systemd[1]: mysql.service: Failed with result 'exit-code'.
```

I don't get the sentences before "then you can remove the .ibd file..."

# ls /var/lib/mysql/*.ibd |wc -l
67 

What should I do now?

---

### Post by ELMIT on 2016-11-01
I found on the Internet, and that seems to work:

added into /etc/my.cnf the two lines:

> [mysqld]
innodb_force_recovery = 1

and started the server again.

I removed my.cnf file and restarted mysql again.

It seems to work again.

---

### Post by wwwindisch on 2016-11-01
Dear community,

I had a similar problem on my server twice, already. And I expect it to happen again in the future, since there will be sudden power interruptions every now and then (It's just the way it is, I don't want to start a discussion on UPS etc. here...).
My quick solution so far: stop mysql server --> restore the ibdata1 in /var/lib/mysql/ from backup --> start mysql server --> Done!

**My question:** Are there any options / parameters / tools that can help to reduce the risk of database damage due to sudden power interruptions (even at the cost of performance)? Is there maybe a way to increase storage / disk write frequency such that the likeliness of data loss is reduced or something like that?

Thanks in advance!

---

### Post by ELMIT on 2016-11-01
Something still wrong!!!

I get now "Table is read only". How to fix that?

---

### Post by ELMIT on 2016-11-01
I tried to use in my.cnf all values from 1 to 6 for 

```
[mysqld]
innodb_force_recovery = 1 
```

started mysql, stopped it, set it to 0 and started it again, but still the same 

> #1036 - Table 'gain' is read only

All files are unchanged owner mysql:mysql
All directory permissions of each database is 700
All files within these database directories are 660

I cannot see anything, can you?

---

### Post by ELMIT on 2016-11-05
I was asked to provide the error log file. Maybe that would reveal the reason of not being able to write to the tables. I cannot figure out how to get that one.

ps ax|grep mysql

 7257 pts/24   S+     0:00 grep --color=auto mysql
27540 ?        S      0:00 /bin/bash /usr/bin/mysqld_safe
27541 ?        S      0:00 logger -p daemon err -t /etc/init.d/mysql -i
27700 ?        Sl     3:02 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql **_--skip-log-error_** --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
27701 ?        S      0:00 logger -t mysqld -p daemon error

Here you can see --skip-log-error   
From where does this come from?

grep error.log /etc/mysql/mariadb.conf.d/mysqld.cnf 

log_error = /var/log/mysql/error.log
root@ronald-desktop:/etc/init.d# grep general_log /etc/mysql/mariadb.conf.d/mysqld.cnf 
general_log_file        = /var/log/mysql/mysql.log
general_log             = 1


ls -l /var/log/mysql/
total 4
-rw-r----- 1 mysql adm  0 11&#26376;  5 08:00 error.log
-rw-r----- 1 mysql adm  0 11&#26376;  4 07:41 error.log.1
-rw-r----- 1 mysql adm 20 10&#26376; 19 07:37 error.log.8.gz

---

