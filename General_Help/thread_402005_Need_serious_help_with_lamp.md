---
title: "Need serious help with lamp"
date: 2007-04-05
forum: General Help
---

### Post by bdemers on 2007-04-05
I'd like to build up a community web server.  I'm pretty sure that I want to use YACS (Yet Another Community System).  Problem is I'm a newbie, and as a result not quite sure how to approach this project.  So far I have a server installation, using the LAMP option.  I did put in Gnome so I can use the server for development, since it is running on my intranet.  I believe that the next step for me is to do whatever I need to do to Apache, MySql, and PHP.  So what do I need to do?  All I know for sure is that I need to create a database.  Are there any additional administration type apps that I should install that would ease working with Apache, MySql, and PHP?  See the newbie sticking out?



After prepping the server, then I can repost for help on YACS. like is it supported by the Ubuntu community?

---

### Post by az on 2007-04-05
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Do this:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

This installs the LAMP stack on your system.

Then type

mysql -u root 
(at the prompt type - edit accordingly)
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');

This sets a password for mysql.  You shouldn't leave it without a password.

then,
CREATE DATABASE database1;

This creates a database for you to use for your web application.  Call it something else if you like.

then, 
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON database1.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword';

This sets up a mysql user (non-root) with a more limited set of privileges to use the database.  Chance the username and password to what you like.

The go to yoursite/yacs/setup.php and follow the instructions.

I never used it before, I just read the docs.  It is similar to Drual or any other web application on LAMP.


[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

---

### Post by bdemers on 2007-04-05
Thank you for the info.  For sure Linux is not short on documentation, finding it though can be something of a challenge.  A community forum such as this is huge.  Please, stick around.

---

