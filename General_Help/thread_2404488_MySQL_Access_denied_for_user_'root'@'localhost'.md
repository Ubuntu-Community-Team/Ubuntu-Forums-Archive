---
title: "MySQL Access denied for user 'root'@'localhost'"
date: 2018-10-24
forum: General Help
---

### Post by fennrir on 2018-10-24
Hello. I'm really new in Ubuntu and I tried installing MySQL. When I try to access it with ```
mysql -u root -p
``` command I get this error: ```
ERROR 1698 (28000): Access denied for user 'root'@'localhost'
```. Following advice form the internet I tried with ```
sudo mysqld_safe --skip-grant-tables
``` but then I get this ```
2018-10-24T18:45:05.327382Z mysqld_safe Logging to syslog.
2018-10-24T18:45:05.337985Z mysqld_safe Logging to '/var/log/mysql/error.log'.
2018-10-24T18:45:05.348007Z mysqld_safe Directory '/var/run/mysqld' for UNIX socket file don't exists.

```

Oh and I tried setting new password with ```
sudo mysql_secure_installation 
``` but it didn't help.
Any ideas?

---

### Post by yancek on 2018-10-24
> mysql -u root -p

Before doing this, did you run mysql_secure_installation and did you create a password for root.  You could also do it with:  mysql -u root and you should then get a mysql prompt (mysql>) where you would enter:   SET PASSWORD FOR 'root'@'localhost' = PASSWORD('actualpassword');  You might need to run  flush privileges from the mysql prompt.

---

### Post by fennrir on 2018-10-25
> **yancek said:**
> Before doing this, did you run mysql_secure_installation and did you create a password for root.  You could also do it with:  mysql -u root and you should then get a mysql prompt (mysql>) where you would enter:   SET PASSWORD FOR 'root'@'localhost' = PASSWORD('actualpassword');  You might need to run  flush privileges from the mysql prompt.

As I said in my post yes, I did set a password with ```
mysql_secure_installation
``` and when I enter this password the access is still denied. When I try  ```
mysql -u root
``` it gets denied as well.

---

### Post by yancek on 2018-10-25
You might try using sudo with the command and reading the other possible solutions at the link below.

 [https://askubuntu.com/questions/1029177/error-1698-28000-access-denied-for-user-rootlocalhost-at-ubuntu-18-04](https://askubuntu.com/questions/1029177/error-1698-28000-access-denied-for-user-rootlocalhost-at-ubuntu-18-04)

---

### Post by fennrir on 2018-10-25
Ok I found the solution right here

[https://stackoverflow.com/questions/41984956/cant-reset-root-password-with-skip-grant-tables-on-ubuntu-16](https://stackoverflow.com/questions/41984956/cant-reset-root-password-with-skip-grant-tables-on-ubuntu-16)

---

