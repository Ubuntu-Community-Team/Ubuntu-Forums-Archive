---
title: "PHPMyAdmin broken since 7.04 upgrade"
date: 2007-04-29
forum: General Help
---

### Post by UbuntuniX on 2007-04-29
Since I've upgraded to Feisty, PHPMyAdmin won't work. Every time I try to login to it (as root or normal user), I get this error message:

> 
Error
#1045 - Access denied for user 'www-data'@'localhost' (using password: YES)


MySQL itself is working fine, as I can do everything via command line, and a phpBB3 forum I installed is still running.

Any ideas? =\


Edit: Also, I've tried reinstalling & complete removal...

---

### Post by UbuntuniX on 2007-05-09
Bump. I've since reinstalled Ubuntu, and found PHPMyAdmin still giving me this error.

---

### Post by ikonia on 2007-05-09
I was working on this with someone in the irc channel today, but he had to leave.

This seems a bit of a strange one.

Lets try to get to the bottom of it so we can log an accurate bug.


First things first.

1.) check you can connect to the mysql database using the same connection string as myphpadmin

> 
mysql -u www-data -h localhost -p 


you'll be prompted for the password and see if it connects, 

then do a "show databases" to prove your connected fine.

Please also post the output of "ps -ef | grep mysql" into your response.

Then we can take if from there.

---

### Post by ikonia on 2007-05-09
Also - did you install all this as a "lamp" install in fesity,or manually get php, mysql, myphpadmin from the ubuntu repo's.

---

### Post by UbuntuniX on 2007-05-09
> **ikonia said:**
> I was working on this with someone in the irc channel today, but he had to leave.

This seems a bit of a strange one.

Lets try to get to the bottom of it so we can log an accurate bug.


First things first.

1.) check you can connect to the mysql database using the same connection string as myphpadmin



you'll be prompted for the password and see if it connects, 

then do a "show databases" to prove your connected fine.

Please also post the output of "ps -ef | grep mysql" into your response.

Then we can take if from there.

ERROR 1045 (28000): Access denied for user 'www-data'@'localhost' (using password: YES)

> **ikonia said:**
> Also - did you install all this as a "lamp" install in fesity,or manually get php, mysql, myphpadmin from the ubuntu repo's.

I'm not using Ubuntu strictly as a server, so I'm using the desktop edition with packages from the repositories.

---

### Post by ikonia on 2007-05-09
fantastic, ok, your problem looks slightly different.

looks like your mysql www-data user doesn't have access to admin the database.

you need the mysql grand option

connect to mysql as the mysql root user

> 
mysql -u root -h localhost -p



then grant your use permissions

> 
GRANT ALL PRIVILEGES on *.*  TO 'www-data'@'localhost' IDENTIFIED BY 'a password';
FLUSH PRIVILEGES;


try connecting as the www-data user on the command line again and lets see how it goes.

---

### Post by UbuntuniX on 2007-05-09
> **ikonia said:**
> fantastic, ok, your problem looks slightly different.

looks like your mysql www-data user doesn't have access to admin the database.

you need the mysql grand option

connect to mysql as the mysql root user




then grant your use permissions



try connecting as the www-data user on the command line again and lets see how it goes.

That didn't work. www-data is the error for any user, not an actual user.
MySQL is not the problem. PHPMyAdmin is. MySQL itself is fine.

---

### Post by ikonia on 2007-05-09
Hi,

I think you've missunderstood whats going on here.

I'll try to clarify and if I'm wrong in my assumptions please provide the log/code to show the correct response.

the user "www-data" is the user your webserver is running as. (At a Unix account level). When myphpadmin attempts to make a connection through the web interface, the unix user running the web interface is launching the connection, and mysql connection is assuming its username

eg: if apache was run by the user jimbo - then the user jimbo would be passed to mysql.

> 
unix-dev@puzzle:~$ ps -ef |grep apache
root      4652     1  0 May08 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  4704  4652  0 May08 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data  4705  4652  0 May08 ?        00:00:01 /usr/sbin/apache2 -k start -DSSL
www-data  4706  4652  0 May08 ?        00:00:01 /usr/sbin/apache2 -k start -DSSL
www-data  4707  4652  0 May08 ?        00:00:01 /usr/sbin/apache2 -k start -DSSL



There are two ways around this

1.) give the mysql user "www-data" full admin control over the database
2.) change the user myphpadmin connects as to "root"

option 1 is the easiest.

To do this - do the grant command I've posted above, then test this using the mysql command

> 
mysql -u www-data -h localhost -p


and enter the password you assigned in the grant option. If this works you're fine at the mysql level and you can start debugging the myphpadmin issues.

Does that make sense to you ?

---

### Post by strixy on 2007-05-09
I had a similar problem. Did you install phpmyadmin using synaptic or apt-get?

I did. It didn't work. I got similar errors.

I completely removed phpmyadmin, removed the redirects in etc/apache2/sitesenabled/default; reinstalled phpmyadmin by downloading the .tar from it's project page on sourceforge and manually installed it to /var/www/phpadmin. (not localhost/phpmyadmin - make something up that's not so easily guessed by the casual luser)

Following along with the install manual that comes with phpmyadmin, I did the usual chown/grp/770 thing

chown -R www-data /var/www/phpadmin
chgrp -R www-data /var/www/phpadmin
chmod -R 770 /var/www/phpadmin

browsed over to localhost/phpadmin and voila!

---

### Post by eschatron on 2007-05-09
I had the same problem, strixy's solution worked.  Additionally I didn't even have to reinstall, just updated the ownership/permissions as he describes.

---

### Post by UbuntuniX on 2007-05-09
> **ikonia said:**
> There are two ways around this

1.) give the mysql user "www-data" full admin control over the database
2.) change the user myphpadmin connects as to "root"

option 1 is the easiest.

To do this - do the grant command I've posted above, then test this using the mysql command



and enter the password you assigned in the grant option. If this works you're fine at the mysql level and you can start debugging the myphpadmin issues.

Does that make sense to you ?

www-data already had full control, and I've tried with root.

I'll try the suggestion of downloading the source from their site. I used Synaptic/Apt-Get before.

---

### Post by ikonia on 2007-05-09
whoaaaa whoaaa whoaaaa

don't download the source package and break your dependency tree.

Lets work this through and either fix it or log a bug to get it fixed so the ubuntu community can benifit.

Let me get the facts clear

1.) you can connect with "mysql -u www-data -h localhost -p" and then do say "show databases" all that works
2.) when you try to connect using myphpadmin what username and parameters are you specifying to connect
3.) What is the exact error message
4.) what does /var/log/mysql.log and /var/log/mysql.err say 
5.) if your getting no output alter the mysql init script to do "mysqld -log" then tail the log file for output when you do a connect using myphpadmin, compare that against when you do a connect from the command line.


Please, lets work this through rather than having a problem and dropping it so no-one else can benifit.

---

### Post by strixy on 2007-05-09
Working through the problem is a good idea to be sure, but a work around until that problem is fixed is important also.  I'll happily support your efforts to debug this issue.

---

### Post by ikonia on 2007-05-10
yup, 

I'm happy to work this through as it looks like the package has a problem and it would be good to get it resolved.

I'll install it on my box at home to work this throguh myself but in the meantime it would be good if the origional poster could provide feedback to the questions.

---

### Post by erwin.wernsen on 2007-05-10
Hi,

I had the similar problems logging in on phpmyadmin. For me installing php5-mcrypt solved it. I use the 64bit version of ubuntu feisty.

regards,

Erwin

---

### Post by UbuntuniX on 2007-05-11
> **erwin.wernsen said:**
> Hi,

I had the similar problems logging in on phpmyadmin. For me installing php5-mcrypt solved it. I use the 64bit version of ubuntu feisty.

regards,

Erwin

Yes, I'm also using 64bit, and that fixed. Thanks! :)

Thanks everyone else, too. ;)

---

### Post by TakeshiKovacs on 2007-05-18
Same problem here and the 

[PHP]sudo apt-get install php5-mcrypt[/PHP]

solved the problem for me as well. 

Bit odd if you ask me.

Anyway, what can we do, that this really nasty problem gets fixed?

---

### Post by stevermeeks on 2007-07-13
aaaaaaaaaaaaah! yes, thank you, i too have been trying to fix this problem with the 64 bit version, read through all documentation in both MySQL and PhPmyadmin, to no avail until now, thanks

---

