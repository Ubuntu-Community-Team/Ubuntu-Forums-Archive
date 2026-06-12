---
title: "Apache2 PHP Connect to DB clears rest of screen"
date: 2014-02-21
forum: General Help
---

### Post by Brandon_Krous on 2014-02-21
Whenever I attempt to connect to a database (both sqlite3 and MySQL) in a php script, it does not connect and clears everything after it on the page.

So the following works and this will print hello twice on the screen:
<?php
echo 'hello';
?>
<h1> hello </h1>

But as soon as I give any commands to connect to a database, It will not display anything after the command:
<?php
$con=mysqli_connect("example.com","user","pass","my_db");
echo 'hello';
?>
<h1> hello </h1>

It will not display hello on the screen afterwards, nor will it give any errors on the screen or in the logs.

MySQL and SQLite are installed and working.

Any Ideas? I am completely lost.

Thanks!

---

### Post by dragonfly41 on 2014-02-21
I don't know if this is just a typo error in your post .. but I see a rogue space in your command

$con=mysqli_connect("example.com","user","pass","m y_db");
                                                                         [COLOR=#ff0000][/COLOR]
Your database would not be found.

---

### Post by al3arbe1 on 2014-02-21
For display errors

Try:
```
gksudo gedit /etc/php5/apache2/php.ini
```
Or
```
sudo gedit /etc/php5/apache2/php.ini
```

Find:
```
display_errors = Off
```
Replace to
```
display_errors = On
```

Restart Apache
```
sudo service apache2 restart
```

---

### Post by Iowan on 2014-02-21
[Recommendation]("http://www.psychocats.net/ubuntu/graphicalsudo") is to use **gksudo** with **gedit**.

---

### Post by al3arbe1 on 2014-02-21
Hi lowan,
Thanks
gksudo not installed on ubuntu

---

### Post by SeijiSensei on 2014-02-21
Also, you should test that the connection was made successfully like this:
```

<?php
$debug = 1;

$con=mysqli_connect("example.com","user","pass","m y_db");
if ($con && $debug) { 
    echo "Connected to database!";
} else if ($debug) {
    echo "Could not connect to database!!!";
}
?>

```
The _connect functions return either a resource pointer or FALSE if no connection can be made.  Setting debug to zero will turn off the announcements.

---

### Post by Brandon_Krous on 2014-02-22
Sorry. Yeah, that's just a typo in the post. Thank you though!

---

### Post by Brandon_Krous on 2014-02-22
I removed then re-added apache2, php5 and mysql and it is magically working again. Everything displays as it should! Thank you a million for everyone's help!!

---

