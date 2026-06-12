---
title: "MySql"
date: 2005-06-21
forum: General Help
---

### Post by mgway on 2005-06-21
Okay. 
I set up MySql using the #sudo apt-get method. 
Now what do I do... How can I configure the login/passwords so that I can set up phpBB?
Any help would be greatly appreaciated. 
Thanks.

---

### Post by az on 2005-06-21
Sorry, but I do not have mysql installed on this particular machine.

Look in /usr/share/doc/mysql

The readme tells you how to set the root(not the linux root user, but the mysql root user) password

I think it is something like
mysqladmin -u root password (password)

---

### Post by deBaas on 2005-06-21
You can only use the command line for that. If you want a nice GUI for mysql I recommend installing phpmyadmin

---

### Post by mgway on 2005-06-21
*tries*
Well, I did the command. And it looks like it went through...
Except when I try to set up phpBB...it fails. 
=|

---

### Post by qd989 on 2005-06-21
open up mysqld's tcp port and install SQLyog onto your windows machine from

[http://www.webyog.com/sqlyog/index.php](http://www.webyog.com/sqlyog/index.php)

I haven't found a good non-windows tool yet... still looking

---

### Post by az on 2005-06-21
[QUOTE=mgway]*tries*
Well, I did the command. And it looks like it went through...
Except when I try to set up phpBB...it fails. 
=|[/QUOTE]

What do you mean. What is the error?

---

### Post by afonic on 2005-06-22
sudo apt-get install phpmyadmin

Then load phpmyadmin (it will be in [http://localhost/phpmyadmin](http://localhost/phpmyadmin)) and login as user "root" with blank password. Then give root users a password, delete the "Any" entries having read access from % and add a new user for phpBB as well as a new database.

---

### Post by mgway on 2005-06-22
Ahh. 
I installed phpMyAdmin. 
It works now. 
Just nobody can connect. =(

Anyone know how to open port 80 on Ubuntu? Because I've got my router port open to all ports (DMZ) but it won't connect.

---

