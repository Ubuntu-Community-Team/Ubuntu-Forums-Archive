---
title: "Can't connect to local MySQL server through socket /tmp/mysql.sock"
date: 2007-10-30
forum: General Help
---

### Post by justin4480 on 2007-10-30
I'm relatively new to Linux, so bit of a newbie warning!!

I've installed php5 and phpMyAdmin (MySQL) via synaptics.  Both seem to work fine on their own, but when running a php mysql_connect() I get a socket error (see below).

I've spent hours forum searching and tried a few things, but no luck.

I have included as much information as think will be relevent.



THE ERROR MESSAGE
-----------------

mysql_connect($dbhost, $dbuser, $dbpass) causes:

Debug Warning: /var/www/jwgodfrey/include.php line 28 - mysql_connect() [<a href='function.mysql-connect'>function.mysql-connect</a>]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)



INSTALLED
---------

Ubuntu 7.10, Php5, PhpMyAdmin, Zend Studios 5.5.0



LOCATION 'php.ini'
------------------

/etc/php5/apache2/php.ini
and the socket is left null for default: mysqli.default_socket =



LOCATION 'my.cnf'
-----------------

/etc/mysql/my.cnf

[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking



LOCATION 'mysqld.sock'
----------------------

/var/run/mysqld/mysqld.sock

I also have a mysql.sock broken link:
Location: 	/var/lib/mysql
Link target:	/tmp/mysql.sock

---

### Post by stump138 on 2007-10-30
First make sure that iptalbes is accepting on your mysql port.  You may need to open it.

2nd, what are the parameters you are passing to the mysql_connect() function?

---

### Post by justin4480 on 2007-10-30
Firstly:  Sorry, I have no idea what an iptalbes is.  How would I check this?


Secondly:

@define ("DBHOST", "localhost");
@define ("DBNAME", "jwgodfrey");
@define ("DBUSER", "root");
@define ("DBPASS", "*******");

// Database connect function
function db_connect($dbname = DBNAME, $dbuser = DBUSER, $dbpass = DBPASS, $dbhost = DBHOST)
{
    $conn = @mysql_connect($dbhost, $dbuser, $dbpass) or DIE("DATABASE CONNECTION ERROR");
    @mysql_select_db($dbname, $conn);
    return $conn;
}

---

### Post by stump138 on 2007-10-30
iptables is the built in firewall that comes standard in ubuntu.  If you are using the standard mysql port open a terminal and try this:

sudo iptables -A INPUT -p tcp --dport 3306 -j ACCEPT
         and
sudo iptables -A INPUT -p udp --dport 3306 -j ACCEPT

that should open up your firewall for tcp and udp requests for mysql ports

ok..for your mysql_connect(), try this out and see how it goes, simply remove the variables and do them as literals.

mysql_connect(localhost, $mysql_user_name, $mysql_password)

---

### Post by justin4480 on 2007-10-30
Yes, it is using port 3306 (or so the my.cnf file states).

I added the two 'iptables' commands and removed the variable from the mysql_connect but problem persists.

---

### Post by stump138 on 2007-10-30
Provided mysql is up and running, normally I find this to be a syntax issue :\

I would try this next:

mysql_connect("localhost", "username", "password");

other than that, I would replace "localhost" with "127.0.0.1".  I'll start digging around in my php/mysql server setup and see if I can replicate your error.

---

### Post by justin4480 on 2007-10-30
ohh, having changed localhost to 127.0.0.1 I no longer get the same error.  Now it says:

Debug Warning: /var/www/jwgodfrey/include.php line 28 - mysql_connect() [<a href='function.mysql-connect'>function.mysql-connect</a>]: Client does not support authentication protocol requested by server; consider upgrading MySQL client

FYI.  I'm running:

phpMyAdmin - 2.10.3deb1
MySQL client version: 5.0.45

---

### Post by stump138 on 2007-10-30
Is your PhpMyAdmin connecting successfully and letting you alter the db?and have you checked the mysql error code?

mysql_connect("localhost", "username", "password") or die(mysql_error());

That might spit out a bit more information that would be useful to you.

If your phpmyadmin is working properly, you can steal the settings that they are using to connect and run your db.

---

### Post by justin4480 on 2007-10-30
> **stump138 said:**
> Is your PhpMyAdmin connecting successfully and letting you alter the db?and have you checked the mysql error code?

Yes, PhpMyAdmin is working fine. I can create & alter DB's

And yes.  Have been searching on that recent error.


> **stump138 said:**
> mysql_connect("localhost", "username", "password") or die(mysql_error());

That might spit out a bit more information that would be useful to you.

Good thinking.  But it doesn't appear to output anything.


> **stump138 said:**
> If your phpmyadmin is working properly, you can steal the settings that they are using to connect and run your db.

I have no idea how I would do this.


**Key new information.**  Having created a new user 'justin' within phpMyAdmin WITHOUT a password, it works correctly!!  Obviously this isn't really a fix as I need a password

---

### Post by justin4480 on 2007-10-30
Found the Fix!!!


**The Problem**

PHPMyAdmin has been setup to use "cookie" authentication, but when you try to log into phpmyadmin, it returns:

"Client does not support authentication protocol requested by server; consider upgrading MySQL client"


**The Fix**

This is because, the mysqlclient installed on the box does not use the same authentication protocol that the mysqlserver is using. You can either upgrade the client, or reset the root password using this

SET PASSWORD FOR user@localhost = OLD_PASSWORD('password');


Thank you so much for your help Stump138, wouldn't have got to this without your help!!


Referenced fix from: [http://www.megalinux.net/archives/463.html]("http://www.megalinux.net/archives/463.html")

---

