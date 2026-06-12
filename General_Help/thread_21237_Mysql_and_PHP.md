---
title: "Mysql and PHP"
date: 2005-03-21
forum: General Help
---

### Post by Kanna on 2005-03-21
Hello

I experiance some problems using mysql and PHP. I installed the packages with apt-get following the ubunto guide. but when I try to connect to it with a simple php script it gives me:

Fatal error: Call to undefined function: mysql_connect()

I think its some library I am missing? or something that needs to be edited in php.ini? But I havent been able to find exactly what to do to solve it, any help would be appreciated.

Thanks in advance.

---

### Post by TjaBBe on 2005-03-21
[QUOTE=Kanna]Hello

I experiance some problems using mysql and PHP. I installed the packages with apt-get following the ubunto guide. but when I try to connect to it with a simple php script it gives me:

Fatal error: Call to undefined function: mysql_connect()

I think its some library I am missing? or something that needs to be edited in php.ini? But I havent been able to find exactly what to do to solve it, any help would be appreciated.

Thanks in advance.[/QUOTE]

PHP supports mysql functions by default, so I don't expect you're missing a library. Have you configured mysql? (At least added a root password?) I take php runs, seen as you get a php error message, but does the mysql service run? I am not on a Linux system right now so I'm afraid I can't be more specific.

---

### Post by Kanna on 2005-03-21
PHP works fine, I tried some scripts and apache works too.
I set the root password in mysql and created a database, but not more then that. Checking with the ps command I can see that everything is running.

I am using php 4
mysql 4.1
and apache 2
if that is any help.

Thanks for the replay.

---

### Post by TjaBBe on 2005-03-21
[QUOTE=Kanna]PHP works fine, I tried some scripts and apache works too.
I set the root password in mysql and created a database, but not more then that. Checking with the ps command I can see that everything is running.

I am using php 4
mysql 4.1
and apache 2
if that is any help.

Thanks for the replay.[/QUOTE]

Hmm... That is strange... It could be that you need to include a module for mysql into php, I can't remember doing something like that myself though... What does phpinfo(); say regarding mysql?

---

### Post by Kanna on 2005-03-21
since this is more or less for testing I dont mind showing you the phpinfo()

you can see it at: [http://213.66.87.111/info.php](http://213.66.87.111/info.php)

The info on the page is rather confusing for me though  :-)

---

### Post by TjaBBe on 2005-03-21
[QUOTE=Kanna]since this is more or less for testing I dont mind showing you the phpinfo()

you can see it at: [http://213.66.87.111/info.php](http://213.66.87.111/info.php)

The info on the page is rather confusing for me though  :-)[/QUOTE]

Seems pretty normal, it is compiled with mysql and stuff... My own server is set for a re-install (wich I'll start today) and if I run across any specialties, I'll let you know.

---

### Post by brousch on 2005-03-22
Can you post the php file you are trying to use to connect? It may just be a problem with your php file.

---

### Post by dewey on 2005-03-22
Not to sound mean, but are you sure that you have php4 and not 5 installed?
php5 by default, does not include mysql functions.

```
2.  Does MySQL work in PHP 5? It seemed to have disappeared.

MySQL is supported with the only change being that MySQL support is no longer enabled by default in PHP 5. This essentially means that PHP doesn't include the --with-mysql option in the configure line so that you must now manually do this when compiling PHP.
```

[edit:]I checked, and you ARE running php4, check to make sure php is looking for mysql in the right dir? [/edit]
I'd also happily take a look at the php code that isn't working for you.

---

### Post by TjaBBe on 2005-03-23
Try to uncomment the following line in /etc/php4/apache2/php.ini:

```

extension=mysql.so

```

And if that doesn't work for you read [this](http://www.ubuntuforums.org/showthread.php?p=103177#post103177) thread. I hope the first options does it for you though because the way suggested in that other thread seems nasty to me.  :-#

---

### Post by Kanna on 2005-03-23
THE php/sql is very simple just to test it, it looks like this:

<html>
<?php
$username="username";
$password="password";
$database="database";

mysql_connect(localhost,$username,$password,$database);
phpinfo()
?>
</html>

I tried to edit the php.ini and add the extension but no luck. 
can errors like this occur depending on which order you install mysql/apache and php?

since I havent really done any work on that computer I am thinking about just reinstalling Ubuntu, I hope that would solve it =)

---

### Post by brousch on 2005-03-23
[I]<?php
$username="username";
$password="password";
$database="database";

mysql_connect(localhost,$username,$password,$datab ase);
phpinfo()
?>[/I]

There is a problem with your database connection command.

Your mysql command should be:
[FONT=Courier New]mysql_connect('localhost', $username, $password);[/FONT]

The mysql_connect() command is not used to connect to a specific database, only a server. See [mysql-connect](http://us2.php.net/function.mysql-connect).

You then use mysql_select_db() to specify the database. See [mysql-select-db](http://us2.php.net/manual/en/function.mysql-select-db.php). 

You may be thinking of the PEAR command for php/mysql connectivity, which allows you to do it all in one step? See [PEAR-connect](http://pear.php.net/manual/en/package.database.db.intro-connect.php) .

---

### Post by Kanna on 2005-03-23
I tried to put it the way you suggested, but it still just tells me the functions are undefined no matter what I type in them.

I am going to reinstall things when I get home later. I will let you know how it goes =)

---

### Post by brousch on 2005-03-23
I see no one asked you to verify that you have the **php-mysql** package installed. It is seperate from the php, mysql, and apache packages.

Sorry I didn't ask that earlier, but usually someone beats me to it. ;)

---

### Post by Kanna on 2005-03-23
Actually I dont think I installed any package called that. Is it avalible in apt-get? if so what name? I cant find it when I try using apt-cache search. 

Sorry for all the newbie-ness =)

---

### Post by us3rQUE on 2005-03-24
php4-mysql from apt-get

check out: [http://www.ubuntuguide.org/#installmysqlapache](http://www.ubuntuguide.org/#installmysqlapache)
------------------------------------------------------------------------------------------------
Q: How to install MYSQL for Apache HTTP Server?
------------------------------------------------------------------------------------------------
$ sudo apt-get install libapache2-mod-auth-mysql
$ sudo apt-get install php4-mysql
$ sudo /etc/init.d/apache2 restart
------------------------------------------------------------------------------------------------

---

### Post by ola on 2005-03-24
I'm not sure whats your problem, but you can try to use phpmyadmin (availible through apt).

It's a PHP tool that lets you admin the databases via www ([http://yourURL/phpmyadmin)](http://yourURL/phpmyadmin)). Watch out though, its not encrypted and might be a security risk.. If you have not set a root password for the database you can do that in phpmyadmin (first log in is blank password then).

Another thing that have helped me some times is that is usually installs the things you need for PHP and MySQL.

---

### Post by Kanna on 2005-03-25
I tried to get the php4-mysql package through apt-get, but it keeps telling me the package cannot be found.  I searched for it too but cant find anything like that.

---

### Post by brousch on 2005-03-25
Did you add the extra repositories from the guide?

---

### Post by BloGTK on 2005-03-25
[QUOTE=Kanna]I tried to get the php4-mysql package through apt-get, but it keeps telling me the package cannot be found.  I searched for it too but cant find anything like that.[/QUOTE]

The debs for php4-mysql and phpmyadmin are all in universe right now. I should note that as of last night, phpmyadmin is broken in Hoary as it looks like something is preventing PHP programs from doing database authentication. Anything written in PHP that tries to authenticate against information in a database (like the user tables in MySQL) will silently fail.

---

### Post by Daz on 2005-04-05
Hi,

I have also been having the same problems (under windows though at the moment - not got the web-server set up under Ubuntu yet).

The route of the problem was using MySQL 4.1 with php4.  MySQL 4.1 or above uses a new encryption algorithm for passwords (mysqli) that php4 cannot interpret.  The easiest fix is to upgrade to php5 as that includes support for mysqli.  However, I have found a couple of fixes scattered on the web...

[http://www.tss2000.nl/vbforum/showthread.php?p=717#post717](http://www.tss2000.nl/vbforum/showthread.php?p=717#post717)

I haven't tested it yet, but plan too quite soon!

Let me know if this helps for you.

---

### Post by alain on 2005-05-17
I had the SAME problem as Kanna. This solved the problem for me :

<?php
function open_connection() {
  $host = "localhost:/var/run/mysqld/mysqld.sock";
  $user = "your username";
  $passwd = "your password";
  return mysql_connect($host, $user, $password);
}

$link = open_connection();
echo ($link);
?>

---

### Post by alain on 2005-05-17
Hummm ... the problem is not solved after all.

Previous php-script had a typo whereby the password was not being passed to the mysql_connect() function. When the password is passed as a parameter, without the typo, then the problem comes back. My conclusion thus far is that the connect only works when : (a) localhost is the $host ; and (b) when the $password is NULL. Which is OK for connecting, but is useless when it comes to creating a database or a table because these operations require the user to be authenticated, e.g. with a real password instead of a NULL value.

<?php
function open_connection() {
  $host = "localhost:/var/run/mysqld/mysqld.sock";
  $user = "alain";
  $password = NULL;
  return mysql_connect($host, $user, $password);
}

$mytest = open_connection();
echo ($mytest);
?>

Somebody HELP us ... please! ... I'm going mad!!

---

### Post by MBurger on 2005-06-28
You may have a look at your *etc/php4/apache2/php.ini*. If the line ```

;extension=mysql.so
``` is commented out remove the leading semicolon and do ```
/etc/init.d/apache2 restart
``` 

Helped for me.

Moritz

---

### Post by sinkemlow on 2005-11-22
It's also important to remember that you've a different php.ini used for command line php scripts located in /etc/php/cli. I was pulling hair out for a couple of hours since my phpinfo() through apache shows the mysql information, but my command line stuff would still fail with the "undefined function" error. ;-)

---

### Post by dlocutor on 2006-02-05
.. this is the fix .. you're my hero

---

