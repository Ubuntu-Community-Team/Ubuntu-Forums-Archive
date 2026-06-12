---
title: "Installing Mysql 5.1"
date: 2008-04-20
forum: General Help
---

### Post by jide on 2008-04-20
Hello, 

Have anyone installed Mysql 5.1version on ubuntu? The official Debian package is Mysql 5.0 and not 5.1 which you can install by: ```
 sudo apt-get install mysql-server
```. I used this how-to link: **[http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html](http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html)** as guide but after the installation, I was unable to manually start the database as stated in step 11 using this command:```
 bin/mysqld_safe --user=mysql & 
```

I just want to know how those who made it did it !

Thanks

---

### Post by trippinnik on 2008-04-20
you can start it with this command
```
sudo /etc/init.d/mysqld start
```

---

### Post by ikonia on 2008-04-20
> **trippinnik said:**
> you can start it with this command
```
sudo /etc/init.d/mysqld start
```




no you don't start it like that if you've just installed a binary release.

The guide the original poster is using does not use an ubuntu package or install things to the same location as the ubuntu package, so using the ubuntu init script is not advised.

What issues do you get when using the startup command the guide you are using suggests ?

---

### Post by jide on 2008-04-20
> **ikonia said:**
> no you don't start it like that if you've just installed a binary release.

The guide the original poster is using does not use an ubuntu package or install things to the same location as the ubuntu package, so using the ubuntu init script is not advised.

What issues do you get when using the startup command the guide you are using suggests ?

It always ask for a password:
```

jide@jide-laptop:/usr/local/mysql$ [sudo] password for jide:

```

May be you can check the step 11 of the link I provided earlier because my problem started at that point. I do not know which password it refers to.

Thanks

---

### Post by ikonia on 2008-04-20
ok, well, there are two things to be aware of here.


1.) because your using a binary install of mysql your database schema from the ubuntu install is now %99 usless to you in your current setup. You therefore have to set the mysql "root" (not ubuntu) user password. This is done with "sudo mysqladmin"

2.) from what I'm seeing using sudo to start the daemon natively is passing the startup daemon your username, rather than "root"

Starting the mysqld daemon as root should not ask you for a password, connecting to that database with mysqladmin, or mysql on it's own should prompt you for a password (-u username -p $passworD)

My own opinion - your not advanced enough to be trying to use binary compatible packages on your system, is there a specific reason/problem you upgraded to 5.1 ? what did you need from 5.1 that 5.0 (stable/packaged/compatible ubuntu release) didn't give you.

Be aware that by installing 5.1 your breaking your ubuntu package manager and could potentially break all your software on your ubuntu box.

---

### Post by jide on 2008-04-20
> **ikonia said:**
> ok, well, there are two things to be aware of here.


1.) because your using a binary install of mysql your database schema from the ubuntu install is now %99 usless to you in your current setup. You therefore have to set the mysql "root" (not ubuntu) user password. This is done with "sudo mysqladmin"

2.) from what I'm seeing using sudo to start the daemon natively is passing the startup daemon your username, rather than "root"

Starting the mysqld daemon as root should not ask you for a password, connecting to that database with mysqladmin, or mysql on it's own should prompt you for a password (-u username -p $passworD)

My own opinion - your not advanced enough to be trying to use binary compatible packages on your system, is there a specific reason/problem you upgraded to 5.1 ? what did you need from 5.1 that 5.0 (stable/packaged/compatible ubuntu release) didn't give you.

Be aware that by installing 5.1 your breaking your ubuntu package manager and could potentially break all your software on your ubuntu box.

I need the partition function in mysql 5.1 which is not available in 5.0. I tried further to fix it by passing "mysql" which is the user to the start daemon instead of my ubuntu pwd. I started the server again with the new changes and got this error:
```

080420 21:14:30 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
080420 21:14:30 [ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'
/usr/local/mysql/bin/mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 2)
080420 21:14:30 [ERROR] Aborting

080420 21:14:30 [Note] 
080420 21:14:30 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended

```

Thanks

---

### Post by ikonia on 2008-04-20
again, the error messages are pretty straight forward on this one.

080420 21:14:30 [ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'

the file is missing.

/usr/local/mysql/bin/mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 2

your logging is not setup correctly (the file is not there)

I assume your trying to start it like this mysqld_safe --user=mysql 

you may want to check the ubuntu init script to just see how the environment varible is setup, and look at basic things for yourself like where it expects the my.cnf file to be and your own $PATH

---

