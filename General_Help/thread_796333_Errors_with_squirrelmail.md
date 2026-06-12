---
title: "Errors with squirrelmail"
date: 2008-05-16
forum: General Help
---

### Post by spark01 on 2008-05-16
I am trying to setup squirrelmail with my MYSQL database. I have courier and  postfix both downloaded from the Ubuntu package and squirrelmail downloaded from their site. When I do that test to see if squirrelmail is configured correctly, I get this error message:

Checking database functions...
     PHP Pear DB support is present.
    mysql database support present.

    ERROR: Database error: not found in preferences DSN.

Does anyone know what could be wrong? Thank you in advance for any help! :)

---

### Post by spark01 on 2008-05-16
Anyone?

---

### Post by spark01 on 2008-05-16
Anyone know how I can debug this error or maybe a guide I can use?

---

### Post by Monicker on 2008-05-16
Documentation is a good thing.


Constructing a data source name - [http://www.squirrelmail.org/docs/admin/admin-5.html]("http://www.squirrelmail.org/docs/admin/admin-5.html")


[http://www.squirrelmail.org/plugin_view.php?id=109]("http://www.squirrelmail.org/plugin_view.php?id=109")

---

### Post by spark01 on 2008-05-16
I have already looked through that documentation and am still having problems, I also searched the error on google with no luck..I am very new with linux and servers so i'm a little confused as to how everything works together...like how does squirrelmail check for username and password when logging in? I have created a database called mail with tables domains and users. Then i have another table called squirrel which is set up like the documentation on the squirrelmail site indicates.

---

### Post by Monicker on 2008-05-16
Check your squirrelmail config.php file for the lines where it talks about the dsn.  What do you have for those entries?

The dsn (data source name), is how it knows which database to use, along with the proper credentials for connecting to the tables.

---

### Post by spark01 on 2008-05-16
In my config.php file i have these lines:

$addrbook_dsn = 'mysql://squirrel:mypass@127.0.0.1/squirrel'; 
$prefs_dsn = 'mysql://squirrel:mypass@127.0.0.1/squirrel'; 
$addrbook_global_dsn = 'mysql://squirrel:mypass@127.0.0.1/squirrel';

---

### Post by Monicker on 2008-05-16
Ok. Run these commands from a terminal
```

mysql -u squirrel -p
```

Enter the password for the squirrel account, as listed in the dsn entries you gave.

Does it let you connect to the mysql database?  If not, either the password is wrong on the mysql account is not configured properly.


If it does connect run this:

```
show databases;
```

What is the output?  Type exit to get out of the mysql console interface.

---

### Post by spark01 on 2008-05-16
It does let me connect, then when I type show databases this is my output:

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| squirrel           | 
+--------------------+
2 rows in set (0.00 sec)

---

### Post by Monicker on 2008-05-16
Log back into the mysql console.

```
use squirrel;
show tables;
```

---

### Post by spark01 on 2008-05-16
I got this output:
mysql> use squirrel;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+--------------------+
| Tables_in_squirrel |
+--------------------+
| address            | 
| global_abook       | 
| userprefs          | 
+--------------------+
3 rows in set (0.09 sec)

---

### Post by Monicker on 2008-05-16
Hrmm.  That looks good so far.  Could be an ip mismatch in your dsn.  What do you have for the bind-address in my.cnf?  Are you still running mysql 6.0?

---

### Post by spark01 on 2008-05-20
The bind address in mysql's my.cnf is 127.0.0.1

And I'm running mysql 5 at the moment.  Would it be a version problem?

---

