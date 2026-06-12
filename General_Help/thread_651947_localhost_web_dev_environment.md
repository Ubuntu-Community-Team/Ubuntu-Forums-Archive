---
title: "localhost web dev environment"
date: 2007-12-28
forum: General Help
---

### Post by nami on 2007-12-28
hi,

i have a local development environment setup which lets me develop webpages in php, html, and mysql.  i would like to test sqlite but i don't know how to install it "if it is not already installed".  how do i check if it is installed, if not installed, how do i install it?

thanks

---

### Post by LaRoza on 2007-12-28
> **nami said:**
> hi,

i have a local development environment setup which lets me develop webpages in php, html, and mysql.  i would like to test sqlite but i don't know how to install it "if it is not already installed".  how do i check if it is installed, if not installed, how do i install it?

thanks

```

sudo aptitude install sqlite

```

---

### Post by nami on 2007-12-28
will i need to configure it?

---

### Post by LaRoza on 2007-12-28
> **nami said:**
> will i need to configure it?

No. How would you? There is nothing to configure :)

---

### Post by nami on 2007-12-28
excellent,  thanks for the quick response! :KS

---

### Post by LaRoza on 2007-12-28
> **nami said:**
> excellent,  thanks for the quick response! :KS

Just make sure the language your are using has the libraries to use it. PHP probably has it by default, like everything else.

---

### Post by nami on 2007-12-28
i have php5 and sqlite3 and am getting the following error in php


Fatal error: Call to undefined function sqlite_open() in /var/www/sqlite.php on line 9

the php code looks like this

<?php
// set path of database file
$db = $_SERVER['DOCUMENT_ROOT']."/library.db";

// open database file
$handle = sqlite_open($db) or die("Could not open database");

any ideas?

---

### Post by nami on 2007-12-28
so i tried a simple php test

> <?php

// version
echo "SQLite version: ".sqlite_libversion()."<br />";
// encoding
echo "SQLite encoding: ".sqlite_libencoding()."<br />";

?> 

and it gave back
> 
Fatal error: Call to undefined function sqlite_libversion() in /var/www/sqlite.php on line 4

so i am assuming this means that something is not setup right...

---

### Post by LaRoza on 2007-12-28
[http://www.php.net/sqlite](http://www.php.net/sqlite)

Looking for more specific info...
```

sudo aptitude install php5-sqlite3

```

---

### Post by nami on 2007-12-28
i'm still getting the same error.  do i need to restart or something?

---

### Post by Samhain13 on 2007-12-28
After installing the new module, have your restarted apache?

---

### Post by LaRoza on 2007-12-28
> **nami said:**
> i'm still getting the same error.  do i need to restart or something?

Yes, restart. Sorry.

---

### Post by nami on 2007-12-28
i tried the restart and it didn't work.  seems to be a bug of some sort.  in the end i had to do the following to get it to work...

> sudo aptitude install sqlite
sudo aptitude install php5-sqlite
sudo aptitude install sqlite3
sudo aptitude install php5-sqlite3
sudo /etc/init.d/apache2 restart

for some reason apache would not recognise the pdo drivers if i didn't install sqlite2...

thanks for all the help. :KS

---

### Post by LaRoza on 2007-12-28
> **nami said:**
> i tried the restart and it didn't work.  seems to be a bug of some sort.  in the end i had to do the following to get it to work...

for some reason apache would not recognise the pdo drivers if i didn't install sqlite2...


[https://bugs.launchpad.net/ubuntu/+source/php-sqlite3/+bug/178906](https://bugs.launchpad.net/ubuntu/+source/php-sqlite3/+bug/178906)

I posted this earlier, but edited it out, I shouldn't have.

---

### Post by nami on 2007-12-28
ah.  oh well.  at least it's working.  thanks again! :)

---

### Post by nami on 2007-12-28
i thought, now that it is working, i should be able to remove sqlite2.

> sudo aptitude remove sqlite php5-sqlite
sudo /etc/init.d/apache2 restart

but i was wrong, so i removed the rest of it

> sudo aptitude remove sqlite3 php5-sqlite3

and started again

> sudo aptitude install sqlite php5-sqlite sqlite3 php5-sqlite3
sudo /etc/init.d/apache2 restart

and it worked

---

