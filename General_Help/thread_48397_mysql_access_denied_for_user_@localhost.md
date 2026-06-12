---
title: "mysql: access denied for user @localhost"
date: 2005-07-12
forum: General Help
---

### Post by Zelut on 2005-07-12
I seem to be having some problems setting up mysql-server here on my machine.  I followed the instructions on the ubuntuguide (apache, php, mysql, etc).  Apache is running great as well as php but I need to get mysql running so I can use some apps.

Currently if I try any commands using mysqladmin (ie CREATE, DROP, etc) I get this error:

> mysqladmin: CREATE DATABASE failed; error: 'Access denied for user: '@localhost' to database 'test''

Also, I've installed phpmyadmin and when I try to login I get 'The server is not responding' (but with a #mysqladmin ping  I find that mysqld is alive)

thanks

---

### Post by jeroevi on 2005-07-12
[QUOTE=kuyaedz]I seem to be having some problems setting up mysql-server here on my machine.  I followed the instructions on the ubuntuguide (apache, php, mysql, etc).  Apache is running great as well as php but I need to get mysql running so I can use some apps.

Currently if I try any commands using mysqladmin (ie CREATE, DROP, etc) I get this error:



Also, I've installed phpmyadmin and when I try to login I get 'The server is not responding' (but with a #mysqladmin ping  I find that mysqld is alive)

thanks[/QUOTE]

Goto /etc/mysql/my.cnf and look for the skip-networking flag. You need to comment it out. By default networking is not enabled for security reasons. It took me a day to figure this one out.

regards,
Jeroen

---

### Post by Zelut on 2005-07-12
[QUOTE=jeroevi]Goto /etc/mysql/my.cnf and look for the skip-networking flag. You need to comment it out. By default networking is not enabled for security reasons. It took me a day to figure this one out.

regards,
Jeroen[/QUOTE]
 Well I'm getting closer.  Now I get: #1045 - Access denied for user: 'kuyaedz@localhost' (Using password: YES)

Do I need to change localhost? a password? permissions?...

---

### Post by jeroevi on 2005-07-12
[QUOTE=kuyaedz]Well I'm getting closer.  Now I get: #1045 - Access denied for user: 'kuyaedz@localhost' (Using password: YES)

Do I need to change localhost? a password? permissions?...[/QUOTE]

Try to log in with root and an empty password.
Once logged in to mysql you will need to add a user with the grant sql command or via some GUI like mysql-admin.

---

### Post by Zelut on 2005-07-18
I'm getting access denied for my user as well as root.  I can't seem to get in, period.  Any ideas?

---

### Post by Zelut on 2005-07-18
I've uninstalled & reinstalled apache2, php4 & mysql-server to try & start fresh.  Apache works fine, as does php4 again however I'm still stuck with this mysql access error.  I've tried access via #mysqladmin & phpMYadmin.  Both give me access denied.  I've tried root with & without a password.  Any ideas?  I've tried to set the password but it gives me access denied at that point as well.

---

### Post by apachesoul on 2005-07-25
[QUOTE=kuyaedz]I've uninstalled & reinstalled apache2, php4 & mysql-server to try & start fresh.  Apache works fine, as does php4 again however I'm still stuck with this mysql access error.  I've tried access via #mysqladmin & phpMYadmin.  Both give me access denied.  I've tried root with & without a password.  Any ideas?  I've tried to set the password but it gives me access denied at that point as well.[/QUOTE]
 I have same problem with you but I couldn't solve it, either. Please someone help!

---

### Post by jason_dc on 2005-07-25
I am new to ubuntu, but usually when MySQL is installed on linux the admin user and password are set to user = root password = (no password)


what happens when you just type "mysql" at the command prompt?

or mysql -u root

does this still give you an error?

---

### Post by wrtrdood on 2005-07-25
What happens if you simply type mysql <enter>?

---

### Post by apachesoul on 2005-07-25
[QUOTE=jason_dc]I am new to ubuntu, but usually when MySQL is installed on linux the admin user and password are set to user = root password = (no password)


what happens when you just type "mysql" at the command prompt?

or mysql -u root

does this still give you an error?[/QUOTE]
 apachesoul@apachebase:~$ mysql -u root
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)
apachesoul@apachebase:~$ mysql -u root -p
Enter password:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)
apachesoul@apachebase:~$

If I just type mysql it enters but when I say "CREATE DATABASE EXAMPLE;" same access problem :(

The things that I get are these. I tried to change root's password form users and groups. I did 123456 but still same when I try to enter. By the way I'm login with "apachesoul" on my machine. I've changed "root"s in config.inc.php to "apachesoul". This time I was able to ,enter to phpmyadmin but I had no prieveledge. When I say Create a new database same error occured again. Please help I need mysql to develop a website in a short time.

---

### Post by jason_dc on 2005-07-26
The MySQL accounts are stored in the database "mysql" not the users and groups

when MySQL is installed it creates a root account in mysql database with full permissions for root@localhost

so its the root password in the database that matters not the root account on the system

the database root account is installed with a blank password, unless its been changed with an sql command

I have not installed Mysql on Ubuntu yet and my laptop is at home today, if you have no luck I will install it tonight and take a look

---

### Post by wrtrdood on 2005-07-26
Ok.  So that means that your login ID can enter mysql without a password which is as it should be.  Most likely you have not been granted the correct permissions needed to create databases but that doesn't necessarily mean you can't change it.  You will need to GRANT to your user ID all privileges on the mysql database before you'll be able to do much else.  I'm not in front of my linux box right now so I can't offer much more at this point.  I've had to work through this same problem at one time but it's been a while and I don't want to trust my memory (you got enough trouble as it is)

---

### Post by apachesoul on 2005-07-27
[QUOTE=wrtrdood]Ok.  So that means that your login ID can enter mysql without a password which is as it should be.  Most likely you have not been granted the correct permissions needed to create databases but that doesn't necessarily mean you can't change it.  You will need to GRANT to your user ID all privileges on the mysql database before you'll be able to do much else.  I'm not in front of my linux box right now so I can't offer much more at this point.  I've had to work through this same problem at one time but it's been a while and I don't want to trust my memory (you got enough trouble as it is)[/QUOTE]


apachesoul@apachebase:~$ mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 16 to server version: 4.1.10a-Debian_2ubuntu0.1-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> GRANT ALL PRIVILEGES ON *.* TO 'apachesoul'@'localhost'     -> ;
ERROR 1045 (28000): Access denied for user ''@'localhost' (using password: NO)
mysql> Grant ALL on mysql.* TO root;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'
mysql> Grant ALL on mysql.* TO apachesoul;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'
mysql>



 How can I use GRANT command mysql doesn't allow anything. What a bad luck :( ...
2 times I setup mysql but still same. 

mysqladmin: connect to server at 'localhost' failed (*)
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

is Asterisked line may be clue for errors?
Is it a clue


And...


mysql > show databases;
Empty set (0.01 sec)

---

### Post by wrtrdood on 2005-07-27
Something just occurred to me.  Did you initialize the mysql installation?  There's a script called [COLOR=Navy]mysql_install_db[/COLOR] that sets up the database environment.  If you look at /var/lib/mysql and don't see some files there, this has not been run.  I don't think apt will do this for you but I don't remember. 

  The *show databases* command should not return empty.  The very minimum that you should be seeing is two databases -- mysql and test.



Also look at:  [http://www.ubuntuforums.org/showthread.php?t=52354](http://www.ubuntuforums.org/showthread.php?t=52354)

---

### Post by apachesoul on 2005-07-27
[QUOTE=wrtrdood]Something just occurred to me.  Did you initialize the mysql installation?  There's a script called [COLOR=Navy]mysql_install_db[/COLOR] that sets up the database environment.  If you look at /var/lib/mysql and don't see some files there, this has not been run.  I don't think apt will do this for you but I don't remember. 

  The *show databases* command should not return empty.  The very minimum that you should be seeing is two databases -- mysql and test.



Also look at:  [http://www.ubuntuforums.org/showthread.php?t=52354](http://www.ubuntuforums.org/showthread.php?t=52354)[/QUOTE]
 It s really interesting there are two folders mysql and test. Test folder is empty. Mysql folder is full but when I say "show databases;" result is empty set...

I'm going to be mad.

---

### Post by apachesoul on 2005-07-28
Someone please write me which packages should I install to get success in mysql...

---

### Post by Protonz on 2005-07-30
I followed the install instructions for MySQL found here:
[http://www.ubuntuguide.org/#installmysqldatabaseserver](http://www.ubuntuguide.org/#installmysqldatabaseserver)

I entered in the following line:
```
mysqladmin -u root password db_user_password
```

I thought my root password would be 'password', but it didn't work. However, the password 'db_user_password' seems to work with the root account.

---

### Post by apachesoul on 2005-08-11
Thanks for all your help...

Yesterday I changed my system to RedHat Shrike. Everything seems allright :D

---

### Post by chiok on 2005-10-04
Howdy. I had the same problem and I thought it would be helpful to add each step on how I got this to work. I didn't realise at first that the unofficial ubuntu 5.04 guide sets the root password to 'db_user_password' which was throwing me off.

* Add extra repositories to sources.list
* sudo apt-get install mysql-server
* mysqladmin -u root password db_user_password
* Comment out skip-networking in /etc/mysql/my.conf
* sudo mysql_install_db
* mysql -u root -p
* Enter Password: db_user_password
* mysql> create database whatever;
* mysql> show databases;

---

### Post by Zensunni on 2005-12-13
chiok:

I followed your steps, but when I typed:

"sudo mysqladmin -u root password db_user_password"

I got:

error: 'access denied for user: 'root@localhost' (Using password: NO)'

I typed it exactly as you did, except I put sudo infront of it. Did I miss anything?

---

### Post by dflek on 2006-05-24
hi,

having the exact same problem... can't even get into mysql prompt...
[I]
dusty@ds-ubu:~$ mysql
ERROR 1045 (28000): Access denied for user 'dusty'@'localhost' (using password: NO)
dusty@ds-ubu:~$[/I]

](*,)

---

### Post by adamkane on 2006-05-24
Talk about the hard way.

Install LAMP and phpmyadmin this way:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---

### Post by mrtrick on 2007-05-22
I realize this is a rather old post, but to follow up with a resolution... 

Make sure that your mysqld service is running. I was having the same issues and noticed the daemon wasn't even running. Once you start it, you should be able to log in as the root mysql user with no password

---

### Post by zbog on 2007-11-25
Although MySQL admin account is called root, just like Ubuntu administrative account, that's where the similarities between MySQL and Ubuntu users end. MySQL users are completely unrelated to Ubuntu users!

I used to have the same problem with my MySQL server. Here's how I solved it:
I opened a console and I typed:

# To start repair MySQL, we need to stop it first
## Script to stop mysql server
sudo /etc/init.d/mysql stop

## Start another mysqld instance, but this does not check grants
## (grants are access rights in database terminology).
## This mode is only for troubleshooting, please do NOT use it on a day to day basis
sudo mysqld_safe --skip-grant-tables &


Now start mysql-admin or your favourite MySQL administrative tool, you should be able to login with any user, without password and with full root privileges.
#I haven't tried adding users and grants, will come back and edit this

# When you're done adding users and grants, close the client and run
sudo /etc/init.d/mysql stop

# start normal MySQL Daemon (aka server in Linux terminology)
sudo mysqld

# test your new users and passwords with mysql-admin 
# Or, if you like command line:
mysql -u your_username -p
# you will be prompted for password

On a side note:
1) if mysqld_safe --skip-grant-tables still does not solve the problem try uninstalling mysql-server-5.0 and/or mysql-server-4.1 with Synaptic/Adept or command line:

[I]
sudo apt-get remove mysql-server-5.0 mysql-server-4.1
# when done reinstall the packages:
sudo apt-get install mysql-server-5.0 mysql-server-4.1[/I]

2) When you want to see what MySql related precesses you are running, type this in the command prompt:

# ps aux lists all processes running on your computer, one per line
# grep receives the output from the previous command through a pipe 
(symbolised by |) and then  filters the result using regular expressions to output only the lines that contain the given word
ps aux | grep mysql

---

