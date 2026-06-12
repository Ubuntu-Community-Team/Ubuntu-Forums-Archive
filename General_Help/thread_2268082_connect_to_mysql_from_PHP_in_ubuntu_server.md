---
title: "connect to mysql from PHP in ubuntu server"
date: 2015-03-06
forum: General Help
---

### Post by jayon on 2015-03-06
I built my ubuntu server.
installed PHP and mysql.
Inside Root folder/Var/WWW/.... i have my index.php file...In this file how to connect to Mysql
please just show me the connection!

---

### Post by yancek on 2015-03-06
Do you want to connect to the index.php file that shows the php settings as shown in the code below?  Is this setup on a local machine?  

```
<?php phpinfo(); ?>
```

If you did the installation properly and everything worked, you should be able to open a web browser and enter the following:  [http://localhost/index.php](http://localhost/index.php)
That should show the output including the settings for mysql.  If you are looking for something else, you will need to post more detail on what you have tried and what did not work and what actually happened.  It would also be useful for you to post a link to any web site you used to do the install.

Also, which release of Ubuntu are you using?  Earlier releases had the Apache files under /var/www and 14.04 puts them in the more standard sub-directory; /var/www/html.
Can you log in to mysql from a terminal?  Did you create any users? a database?
If you want to test the connection to a database, the code below should work.  You will need to enter your actual user name, password and database name in quotes and access it from a browser window in the same manner as indicated above, change the name of this file to connect.php.

> <?php
$host = "localhost"; 
$user = "user"; 
$pass = "password"; 
$db = "mydb";
$r = mysql_connect($host, $user, $pass);

if (!$r) {
    echo "Could not connect to server\n";
    trigger_error(mysql_error(), E_USER_ERROR);
} else {
    echo "Connection established\n"; 
}
$r2 = mysql_select_db($db);

if (!$r2) {
    echo "Cannot select database\n";
    trigger_error(mysql_error(), E_USER_ERROR); 
} else {
    echo "Database selected\n";
}
?>

---

### Post by jayon on 2015-03-09
i installed the mysql server from command line.....password was set...then installed the phpmyadmin....
m using in virtual box!!! i will send the screenshot soon for more details! thanks for the reply!

---

### Post by jayon on 2015-03-10
@[COLOR=#DD4814][COLOR=#000000][yancek]("http://ubuntuforums.org/member.php?u=1928724")!!!!!!!!!!!!!!!!!  Thanks a lot....u helped me! it worked :D
[/COLOR][/COLOR]

---

### Post by yancek on 2015-03-10
You're welcome.  Glad you got it going.

---

