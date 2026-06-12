---
title: "MySQL problem"
date: 2004-11-30
forum: General Help
---

### Post by paul.hendrick on 2004-11-30
Hi,
i've installed the necessary packages inorder to run the MamboServer on my machine. For this, I need access to mysql from within mambo, so in the INSTALL file, the first instruction to create the mambo database on localhost is:
$ mysqladmin -u db_user -p create Mambo

but first you need to have "db_user" in your mysql users. so using webmin, I've added db_user, with all permissions. but when i run the mysqladmin command(as above), i get a password prompt. enter the password, then i get:
error: 'Access denied for user: 'db_user@localhost' (Using password: YES)' 

and i've got no idea where to go from there. can anybody offer some advice?
thanks!

---

### Post by karih on 2004-11-30
Hmm yes, I seem to get the same results.
Anyhow, to create database, there is another way.
Do
```
$ mysql -u username -p
```
You will be prompted for password, so type it in and log on.
Then you will have a mysql command line.  Type (without the mysql>)
```
mysql> CREATE DATABASE database_name;
```And it should be ready.
Hope this helps.

---

### Post by paul.hendrick on 2004-12-01
hmm, no luck still.
mysql -u kope_db -p
then enter the password, and i get:
```
ERROR 1045: Access denied for user: 'kope_db@localhost' (Using password: YES)
```

argh, i'm confused by this! :(

---

### Post by p!=f on 2004-12-01
You added db_user but you try to connect with kope_db?
Did you set the password for the db_user/kope_db?
What permissions does the user connecting to the db have?

---

### Post by paul.hendrick on 2004-12-01
yeah, db_user is the example, but i'm actually using kope_db.
the password is set for kope_db, and kope_db has all permissions...weird.

---

### Post by p!=f on 2004-12-01
[QUOTE=paul.hendrick]yeah, db_user is the example, but i'm actually using kope_db.
the password is set for kope_db, and kope_db has all permissions...weird.[/QUOTE]
There must be something with the permissions. Are you sure you have correct permissions on the correct database?

```

mysql> GRANT ALL PRIVILEGES ON mambo.* TO kope_db@localhost IDENTIFIED BY 'password';
mysql> FLUSH PRIVILEGES;

```

---

