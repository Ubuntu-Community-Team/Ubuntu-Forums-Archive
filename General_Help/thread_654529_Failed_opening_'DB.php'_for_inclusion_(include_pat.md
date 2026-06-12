---
title: "Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear"
date: 2007-12-31
forum: General Help
---

### Post by timboellis on 2007-12-31
Last night I installed Ubuntu and server software etc. however when I run a cript I get Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') there is no filer there I have install php rear etc. been all over these forums and the people that have fixed it never said how any suggestions?

---

### Post by stijngysemans on 2007-12-31
-Are you developing the script yourself?
-Test the apache webserver (go to localhost in firefox. normally it should display a paga that apache is installed)
-Write a simple php script that writes "hello world". See if this works.

---

### Post by timboellis on 2007-12-31
Its is a script I downloaded and used successfuly on Win 2k however it is a Linux script

---

### Post by timboellis on 2007-12-31
Well I have fixed the issue by just creating the dir it was wanting and transfering over the db.php file hwoever still not working but I beleive this is another issue with PHP5

---

### Post by freymann on 2007-12-31
There's more to the DB.php package than just that one script.

You need to install the PEAR::DB package. I have to do the same thing eventually, just haven't got around to it.

Search for PEAR DB in the forums and see what comes up.

---

### Post by freymann on 2007-12-31
> **timboellis said:**
> Last night I installed Ubuntu and server software etc. however when I run a cript I get Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') there is no filer there I have install php rear etc. been all over these forums and the people that have fixed it never said how any suggestions?

 Go into System>Administration>Synaptic Package Manager.

Search for "pear"

 Make sure the main pear module is selected, and above that you'll see php-db. Select that too. Install and you're done!

 (I just had to add the php-db package as I already had the main pear module).

---

### Post by timboellis on 2007-12-31
Thanks well here goes again going to do a fresh install then indall Apache mysql etc. again thewn will do what you suggested with the Pear packages however can anyone confirm with me I am installign apache mysql right this is how i amdoing it

[PHP]sudo apt-get install apache2
http://localhost/
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart
sudo gedit /var/www/testphp.php
<?php phpinfo(); ?>
http://localhost/testphp.php
sudo apt-get install mysql-server
gksudo gedit /etc/mysql/my.cnf
bind-address = 127.0.0.1
mysql -u root
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
gksudo gedit /etc/php5/apache2/php.ini
;extension=mysql.so
extension=mysql.so
sudo /etc/init.d/apache2 restart[/PHP]

---

### Post by freymann on 2007-12-31
Your steps look fine to me, although you may find this page useful as reference:

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Good luck!

---

### Post by timboellis on 2007-12-31
Well getting there but for some reason thsi time I am getting 

Error while connecting to MySQL: Access denied for user 'root'@'localhost' (using password: NO)

however my config file as always is

<?php

	$dbServer="localhost";

	$dbUsername="root";

	$dbPassword="password";

	$dbDatabase="refer";

?>

---

### Post by timboellis on 2007-12-31
Sorry being thick editing the wrong conf file

anyhow got this script to work which is the easy one but was getting pera erroers precviously which i am not now so will try the other scripts that i downloaded to see if i can get this to work

---

### Post by freymann on 2007-12-31
> **timboellis said:**
> anyhow got this script to work which is the easy one but was getting pera erroers precviously which i am not now so will try the other scripts that i downloaded to see if i can get this to work

What's a pera error? or do you mean parse errors.

If you're getting those, there's something wrong with the PHP script you are using. But overall, it sounds like you have the tools up and running....

---

### Post by timboellis on 2007-12-31
This is now fixed to an extent stil not working but I am thinking it may be that the reg globals are set to off as far as I am aware they need to be on.

However I think most of my issues came with permissions, as the scripts I was uploading were from a windows server and they had no permissions to speak of so i have just now to prove the case set them all to 777 and all okay,

For reference if someone else gets the issues with DB.php all I done was a fresh install using the commands posted earlier and went through the apts and searched for pear and added anything called pear I knwo its not a great idea but it worked one of the packages done its job

---

### Post by timboellis on 2007-12-31
Also I just set register globals to ON and now all tickey boo.

The permissions is not too much of an issue as the server is for a internet intranet


Thanks to everyone that helped

And a Happy New Year to Everyone

---

### Post by timboellis on 2007-12-31
One other questions where do I find the httpd.cof file assuning there is one the same as windows so i can set up allows and deny;s

---

