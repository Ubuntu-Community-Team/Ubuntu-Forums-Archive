---
title: "change password - mysql"
date: 2016-11-02
forum: General Help
---

### Post by flex567 on 2016-11-02
I installed mysql some time ago and now I would like to start it. 
I tried to start it with: 

```
sudo mysql -u root -p
```

I am prompted for the pass but I don't remember my password anymore. 
How can I reset my password and run the program? 

I tried google solutions but what I tried didn't work.

---

### Post by yancek on 2016-11-02
Have you tried the solution at the link below which is specfic to Ubuntu?

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

If you have, I would suggest trying it again 'carefully' and if it fails, post what happens.  You could indicate what you tried so people don't repeat suggestions.

---

### Post by flex567 on 2016-11-02
@yancek 
In your link, at this line:

```
start the mysql client process using this command
```


I get this error: 

```
mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
[1]+  Exit 1                  sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking


```

How can I solve this?

---

