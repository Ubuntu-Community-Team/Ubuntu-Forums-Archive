---
title: "MySQL Problem: mysqladmin"
date: 2008-06-20
forum: General Help
---

### Post by daemon3 on 2008-06-20
I'm using the instructions on [http://drupal.org/getting-started/6/install/create-database](http://drupal.org/getting-started/6/install/create-database) to set up a mysql database.  However, when I type in ```
mysqladmin -u username -p create databasename
``` I type in my password and get the following error: ```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'username'@'localhost' (using password: YES)'
``` (Of course, I use my own user names :)).
Why is this?  Is it even possible to create a MySQL database on a local machine?  Thanks in advance.

---

### Post by robklg on 2008-06-20
MySQL has its own users. It doesn't use system accounts.

If you have just initialized your database... you only have the root user (kinda).

And also, even if you did create your own user in mysql, does it have the permission to create a database?

Anyway, you didn't :). As it says the password is incorrect... well basically that username doesn't exist. :)

Try -u root instead..

---

### Post by daemon3 on 2008-06-20
Sorry...tried that as well.  I still got the same error.
The wierd thing is...if I run the mysql command I can enter a mysql prompt without error.

---

### Post by robklg on 2008-06-20
Try it again,

without the -p option

If you use -p, and even if you just type ENTER, it will think you are using a password..

without -p, then it will work

you can also just:

$ mysql
> create database my_database;

ofcourse

---

### Post by daemon3 on 2008-06-20
Sorry, I still get the same error...this time, of course, without the password prompt.

---

### Post by robklg on 2008-06-20
what happens if you do?

sudo mysqladmin -u root password

Does it say 'access denied'?

If it does, then you have set a mysql root password... do you remember what it is ?

If you don't remember it, you need to reininitalize it. Using mysql_install_db

---

### Post by daemon3 on 2008-06-20
Yup, access denied.  I'm using the mysql root password, too.

---

