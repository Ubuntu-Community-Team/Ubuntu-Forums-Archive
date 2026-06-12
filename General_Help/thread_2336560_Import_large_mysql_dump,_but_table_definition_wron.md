---
title: "Import large mysql dump, but table definition wrong"
date: 2016-09-09
forum: General Help
---

### Post by ELMIT on 2016-09-09
I have a large database table, which I want to import to MySQL. 

As all such dumps, it starts with a table definition. When I try to import at one field an error occurs. The definition for day of birth is set to:

  `dob` date DEFAULT NULL,

When I run bigdump.php to import the table, I get:

MySQL: Incorrect date value: '0000-00-00' for column 'dob' at row 547

How can I fix that? The sql file is 14 GB !!!! My editor would certainly not be able to handle that size.

---

### Post by steeldriver on 2016-09-09
I don't think it's a matter of the table definition being wrong - it's that your mysql configuration is not recognizing 0000-00-00 as a valid representation of the null datetime field

There may be some info that is of use to you here --> [URL="http://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_no_zero_date"]http://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_no_zero_date
[/URL]

---

### Post by ianhaycox on 2016-09-09
You could try,

```
$ cat bigdump.sql | sed s/0000-00-00/1970-01-01/ | mysql
```

---

### Post by steeldriver on 2016-09-09
FWIW I don't think it's a matter of the table definition being wrong - it's  that your mysql configuration is not recognizing 0000-00-00 as a valid  representation of the null datetime field

---

### Post by ELMIT on 2016-09-09
I read [http://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_no_zero_date](http://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_no_zero_date) and it seems to be the right way. However, I have not found how to use it. 

> NO_ZERO_DATE

The NO_ZERO_DATE mode affects whether the server permits '0000-00-00' as a valid date. Its effect also depends on whether strict SQL mode is enabled.

    If this mode is not enabled, '0000-00-00' is permitted and inserts produce no warning.

    If this mode is enabled, '0000-00-00' is permitted and inserts produce a warning.

    If this mode and strict mode are enabled, '0000-00-00' is not permitted and inserts produce an error, unless IGNORE is given as well. For INSERT IGNORE and UPDATE IGNORE, '0000-00-00' is permitted and inserts produce a warning. 

As of MySQL 5.7.4, NO_ZERO_DATE is deprecated. In MySQL 5.7.4 through 5.7.7, NO_ZERO_DATE does nothing when named explicitly. Instead, its effect is included in the effects of strict SQL mode. In MySQL 5.7.8 and later, NO_ZERO_DATE does have an effect when named explicitly and is not part of strict mode, as before MySQL 5.7.4. However, it should be used in conjunction with strict mode and is enabled by default. A warning occurs if NO_ZERO_DATE is enabled without also enabling strict mode or vice versa. For additional discussion, see SQL Mode Changes in MySQL 5.7.

Because NO_ZERO_DATE is deprecated, it will be removed in a future MySQL release as a separate mode name and its effect included in the effects of strict SQL mode. 


NO_ZERO_DATE   seems to be enabled. How and where do I best "not enable" this mode? Do I do that temporary or permanent?

mysql --version
mysql  Ver 14.14 Distrib 5.7.13, for Linux (x86_64) using  EditLine wrapper

---

### Post by ELMIT on 2016-09-09
I found on the Internet the solution:

mysql --version
mysql  Ver 14.14 Distrib 5.7.13, for Linux (x86_64) using  EditLine wrapper

which mysqld
/usr/sbin/mysqld

mysqld --verbose --help | grep -A 1 "Default options"
Default options are read from the following files in the given order:
/etc/my.cnf /etc/mysql/my.cnf ~/.my.cnf 

mysql -u root -p -e "select @@sql_mode"
Enter password: 
+-------------------------------------------------------------------------------------------------------------------------------------------+
| @@sql_mode                                                                                                                                |
+-------------------------------------------------------------------------------------------------------------------------------------------+
| ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION |
+-------------------------------------------------------------------------------------------------------------------------------------------+

We need to get rid of NO_ZERO_IN_DATE,NO_ZERO_DATE

ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION 

sudo nano /etc/mysql/my.cnf 
added:
!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/

[mysqld]
#
# * Mode Settings by Ronald added
#
sql_mode = "ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"

sudo service mysql restart


That worked!

---

