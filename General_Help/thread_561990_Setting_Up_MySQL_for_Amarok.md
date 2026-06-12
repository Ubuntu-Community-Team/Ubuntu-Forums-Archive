---
title: "Setting Up MySQL for Amarok"
date: 2007-09-28
forum: General Help
---

### Post by wersdaluv on 2007-09-28
According to [http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html) , > How to: set up MySQL Database in Amarok 
I found myself complaining about the slow speed of Amarok. Everything would lag, from playing a song to adding a song to the playlist. Then i remembered when I was setting up Amarok that it let me chose a database, and said the faster ones required extra set up. Of course, I chose the no set up required but slow speed option (SQLlite).

Now, I wanted to switch. And boy am i glad. Everything works as fast as it should.
sudo apt-get install mysql-server mysql-client

now this (replace PASSWORD with your password)

mysqladmin -u root password PASSWORD
then this

mysql -p -u root
CREATE DATABASE amarok;
USE mysql;
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';
FLUSH PRIVILEGES;

In Amarok, go to settings> configure Amarok
Click Collection

Select MySQL.

Use the following settings:
Hostname: 127.0.0.1
Database: amarok
Port: 3306
Username: amarok
Password: Your Password
You're done! Enjoy the speediness!

I screwed up before and I don't want to do the same thing again. For example, I want my password to be **gutsy**, what codes should I enter?  I think, I did not get the howto well enough before that's why I screwed up.

I am thinking of entering...

```
mysqladmin -u root password gutsy
``` and
```
mysql -p -u root
CREATE DATABASE amarok;
USE mysql;
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'gutsy';
FLUSH PRIVILEGES;

```
Note:should the ' be really there?

---

### Post by wersdaluv on 2007-09-28
Also, if I want Amarok to be faster, is MySQL really the right choice or should I use PostgreSQL instead or something?

---

### Post by mrfuzzemz on 2007-09-29
> GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';

Looks good to me. Your password should be in the' like this:

GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'gutsy'; 

 What kind of error(s) are you getting? I just set mine up with MySql and it seems to run very quickly.

---

### Post by wersdaluv on 2007-09-29
> **mrfuzzemz said:**
> Looks good to me. Your password should be in the' like this:

GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'gutsy'; 

 What kind of error(s) are you getting? I just set mine up with MySql and it seems to run very quickly.

Thanks. So that's why I was having problems. I used ```
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY gutsy; 
``` before. By the way, the Amarok on Gutsy seems to have a fast SQLite so I think, I won't be needing MySQL anymore. 

Thanks. 

:KS

---

### Post by gacostac on 2007-10-09
Hi i tried to follow the instuctions and got stucked, im new to ubuntu and have 7.4. Here is the error i get:

gacostac@gacostac-desktop:~$ mysqladmin -u root password ######
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

Can anyone help me?

---

### Post by posterboy on 2007-10-09
I had that problem, too. My mysqld is a part of my lampp stack, and there was NO /var/run//mysqld/mysql.sock. I did have a mysql.sock in a different place, so, make a symlink that links the place it wants it to be, with where it really is.

---

### Post by Eriks_Knor on 2007-10-22
Ok. I've got Amarok installed on my pc. Next I went to configure\install mysql server
I started following the instructions just as they were and got this:

thedane@thedane-desktop:~$ sudo apt-get install mysql-sever mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql-sever
thedane@thedane-desktop:~$ 


Now what?

---

### Post by forestpixie on 2007-10-22
if you typed it I'd guess it was a typo - try server instead of sever

---

### Post by Eriks_Knor on 2007-10-22
> **forestpixie said:**
> if you typed it I'd guess it was a typo - try server instead of sever

*smacks head*

---

### Post by Eriks_Knor on 2007-10-22
Ok...

I installed mysql, but now I have an issue where I can't remember my password I entered in it's initial setup.

How can I change my password without remembering what I entered.

And BTW, I appreciate everybody's help and patience on this. This has been a great community so far.

---

### Post by Eriks_Knor on 2007-10-23
After going into synaptic package manager and completely removing mysql-server and mysql-client, I went to a shell prompt and began a reinstallation

[B]Step 1:
sudo apt-get install mysql-server mysql-client
[/B]
thedane@thedane-desktop:~$ sudo apt-get install mysql-server mysql-client
[sudo] password for thedane:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgpod1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-client-5.0 mysql-server-5.0
Suggested packages:
  mysql-doc-5.0 tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  mysql-client mysql-client-5.0 mysql-server mysql-server-5.0
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/34.4MB of archives.
After unpacking 102MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-client-5.0.
(Reading database ... 111682 files and directories currently installed.)
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.45-1ubuntu3_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.0.45-1ubuntu3_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.45-1ubuntu3_all.deb) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Setting up mysql-client-5.0 (5.0.45-1ubuntu3) ...

Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up mysql-client (5.0.45-1ubuntu3) ...
Setting up mysql-server (5.0.45-1ubuntu3) ...

[B]Step 2:
mysqladmin -u root password <PASSWORD>
[/B]
thedane@thedane-desktop:~$ mysqladmin -u root password visionary
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


In the words of Socrates, "WTF?"
What's going on where I can't set my password?

---

### Post by Klondike on 2007-11-09
That's not the right syntax for inputting your password over the command line.  It's

-u[username] -p[password]

IIRC, there can be a space between -u and the username, but not between -p and the password.  If you just put in -p with no password, it'll prompt you for the password immediately, allowing you the chance to enter it without your password actually appearing on the screen.

---

### Post by Admoseley on 2007-11-10
> **Eriks_Knor said:**
> Ok...

I installed mysql, but now I have an issue where I can't remember my password I entered in it's initial setup.

How can I change my password without remembering what I entered.

And BTW, I appreciate everybody's help and patience on this. This has been a great community so far.

Same thing happened to me... here's how to reset the root mysql password

[http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/](http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/)

---

