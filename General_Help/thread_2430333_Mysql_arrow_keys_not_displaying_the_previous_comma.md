---
title: "Mysql: arrow keys not displaying the previous command and syntax error"
date: 2019-10-31
forum: General Help
---

### Post by zak100 on 2019-10-31
Hi,
I installed mysql on ubuntu 18.04. I can access myql login. But when i am typing command I can't use arrow keys as I used in windows to bring back the past history of commands. I typed edit, it loads the command into vi editor and if I make changes and then exit the editor I can't see my edited command on the sql prompt. Also please guide me how to remove the following syntax error:

```

mysql> create table 'user' ('id' int not null auto increment, 'email' varchar(45) null, 'password' varchar(45) null, primary key('id'));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''user' ('id' int not null auto increment, 'email' varchar(45) null, 'password' v' at line 1
mysql> edit
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''user' ('id' int not null auto increment, 'email' varchar(45) null, 'password' v' at line 1
mysql> 




```

Zulfi.

---

### Post by wildmanne39 on 2019-10-31
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by sdsurfer on 2019-10-31
The arrow key should work to display previous commands in the buffer, can't help with that.

table names and column references don't need quotes, that is most likely the largest part of the error. If you like you can use backticks, which are usually only needed if you use names that conflict with keywords (you shouldn't) or spaces (edit, just retested.) You should be able to assign the primary key in the column definition as follows. Be sure to use an encryption on the password. :-D
```

create table user (id int not null auto_increment primary key, email varchar(45) null, password varchar(45) null);
or
create table `user` (`id` int not null auto_increment primary key, `email` varchar(45) null, `password` varchar(45) null);

```

---

