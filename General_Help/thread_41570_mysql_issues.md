---
title: "mysql issues"
date: 2005-06-14
forum: General Help
---

### Post by boosted on 2005-06-14
how do I list all database names, how do I list all user names?

ok..  I am trying to make this logon php script work but in the setup file it wants the name of my sql database?  I don't know the name!  do I have to create one for this script?  how do I do that?  I loged into mysql.. and got this:

mysql>

but no matter what command I try typing it just does this

mysql>
         >
         >

I tried googling for answers and got some commands like "show databases" but it just does the what i mentiond above?  wtf is going on?  I am a noob to linux and mysql so please help me out here!

I realy need to list the users and the databases and maybe create a databse??

---

### Post by GrumpySmurf on 2005-06-14
Hello.  

When it comes to things like development and database systems, there is no substitute to reading the official documentation for the software/language/product.

[http://dev.mysql.com/doc/mysql/en/index.html](http://dev.mysql.com/doc/mysql/en/index.html)

Is the official MySQL Reference Manual.

That said, here's some MySQL statements that might help you.

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
+--------------------+
2 rows in set (0.04 sec)
mysql> use mysql;
Database changed
mysql> show tables;
+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| columns_priv              |
| db                        |
| func                      |
| help_category             |
| help_keyword              |
| help_relation             |
| help_topic                |
| host                      |
| proc                      |
| tables_priv               |
| time_zone                 |
| time_zone_leap_second     |
| time_zone_name            |
| time_zone_transition      |
| time_zone_transition_type |
| user                      |
+---------------------------+
16 rows in set (0.00 sec)
mysql> select * from user;
```
You'll see the user output listed.  If you aren't comfortable with select statements or don't know the syntax, you should probably spend some time with the documentation for MySQL before you get too involved in your project.

---

### Post by photographer on 2005-06-14
well never forget the semicolon ";" at the end of your command...  ;-)

---

### Post by boosted on 2005-06-14
aahhh!  the semicolin!  heheheh  thats what i was forgetting.. thanks!

---

