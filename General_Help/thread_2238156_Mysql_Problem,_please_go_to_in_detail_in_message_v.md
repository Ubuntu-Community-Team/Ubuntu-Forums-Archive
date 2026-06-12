---
title: "Mysql Problem, please go to in detail in message view"
date: 2014-08-06
forum: General Help
---

### Post by chandrasekhar3 on 2014-08-06
Hi,

    I found this error in mysql installation as below can u suggest me, as i had done some trouble shooting with several scenarios and finally i was not fixed this issue.

     sudo mysql -u root -p
     Enter password: 
     ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)


     sudo service mysql restart
     stop: Unknown instance: 
     start: Job failed to start

Thank You.:mad:

---

### Post by cj13579 on 2014-08-06
Make sure that the */tmp/mysql.sock* file exists. If it doesn't, then you can create it by using:

```
touch /tmp/mysql.sock
```

You can then try starting it in safe mode before starting again in full mode using the command you posted:

```
sudo /usr/bin/mysqld_safe &
```

---

### Post by chandrasekhar3 on 2014-08-07
It is showing the reply like this........................

[1] 11075
sekhar@Vtiger-Admin:~$ 140807 15:29:46 mysqld_safe Logging to '/var/lib/mysql/Vtiger-Admin.err'.
140807 15:29:46 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql.............................and get stucked here.....

touch /tmp/mysql.sock-----------for this one it is not displaying anything....ideal..

---

### Post by cj13579 on 2014-08-07
Yep, I wouldn't expect you to get any output for the touch command. The *&* on the end of the last command makes the program run in the background so I am don't think it is getting stuck. This is just normal StdOut stuff. We can check that it is running by using the following command:

```
ps -ef | grep mysql
```

You can also try logging in to mysql again. You shouldn't need to use sudo to do that.

---

