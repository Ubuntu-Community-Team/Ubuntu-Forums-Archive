---
title: "Error establishing a database connection"
date: 2020-12-01
forum: General Help
---

### Post by hezy2 on 2020-12-01
Hello,
I'm trying to install Wordpress on Ubuntu 20.04.1 and get the above error message. I followed this guide
 [https://ubuntu.com/tutorials/install-and-configure-wordpress#4-configure-database](https://ubuntu.com/tutorials/install-and-configure-wordpress#4-configure-database)
 
and the configurations now are (see attachment)

OS: Ubuntu 20.04.1 (SMP) on OracleVB.  Thanks,
Hezy

---

### Post by SeijiSensei on 2020-12-01
You have to set up the database in MySQL before running the WordPress installer.  Did you follow these steps in the tutorial?

[https://ubuntu.com/tutorials/install-and-configure-wordpress#4-configure-database](https://ubuntu.com/tutorials/install-and-configure-wordpress#4-configure-database)

---

### Post by hezy2 on 2020-12-03
I followed them. You can see in the attachment the localhost.php file

---

### Post by SeijiSensei on 2020-12-03
deleted

---

### Post by SeijiSensei on 2020-12-03
> **hezy2 said:**
> I followed them. You can see in the attachment the localhost.php file

That just shows the definitions that WP uses to connect to the database.  I'm talking about the steps to create the database with the mysql client as described in [https://ubuntu.com/tutorials/install-and-configure-wordpress#4-configure-database](https://ubuntu.com/tutorials/install-and-configure-wordpress#4-configure-database).

What if you run the command "ps ax | grep mysql"? Do you see something like this:
```
$ ps ax | grep mysql
 2734 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe --datadir=/var/lib/mysql --socket=/var/lib/mysql/mysql.sock --pid-file=/var/run/mysqld/mysqld.pid --basedir=/usr --user=mysql
 2950 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib64/mysql/plugin --user=mysql --log-error=/var/log/mysqld.log --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/lib/mysql/mysql.sock

```

If you run the command, "mysql -u root wordpress" what happens?  Use "-p password" as well if you set up a password.  I never bother with database passwords since I only permit connections from the local machine.

---

### Post by hezy2 on 2020-12-04
You're correct. Sorry for no understanding you. During the mysql configuration I got this:

mysql> GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER
    -> ON wordpress.*
    -> TO wordpress@localhost
    -> IDENTIFIED BY 'password';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'IDENTIFIED BY 'password'' at line 4

I guess I just don't type it right

---

### Post by SeijiSensei on 2020-12-05
MySQL usually wants single quotes in the user@host section like this:
```
TO 'wordpress'@'localhost'
```

See [https://dev.mysql.com/doc/refman/8.0/en/grant.html](https://dev.mysql.com/doc/refman/8.0/en/grant.html).

---

