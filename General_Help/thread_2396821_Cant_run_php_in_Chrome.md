---
title: "Cant run php in Chrome"
date: 2018-07-21
forum: General Help
---

### Post by zkab on 2018-07-21
I have 18.04 LTS and installed:

apache2
libapache2-mod-php
php

When I try to run a php script in Chrome with: 'localhost/path-to-script/script.php' I get:

Not Found
The requested URL 'path-to-script/script.php' was not found on this server.
How can I run the php script in Chrome?

---

### Post by dragonfly41 on 2018-07-21
What do you see when you just launch [http://localhost](http://localhost)

Can you run phpinfo()

---

### Post by yancek on 2018-07-21
The standard location for apache files is /var/www/html so is your script.php located there or in a sub-directory?  If it is somewhere else, you would need to manually modify the configuration file of apache.

---

### Post by mIk3_08 on 2018-07-21
> **zkab said:**
> I have 18.04 LTS and installed:

apache2
libapache2-mod-php
php

When I try to run a php script in Chrome with: 'localhost/path-to-script/script.php' I get:

Not Found
The requested URL 'path-to-script/script.php' was not found on this server.
How can I run the php script in Chrome?

what exactly that you are planning to run? if you want to run the php admin, Here [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by zkab on 2018-07-21
1) [http://localhost](http://localhost) gives me - Apache2 Ubuntu Default Page
2) $ phpinfo() gives me a prompt > 
3) When I moved the script to /var/www/html and made it executable and run 'http://localhost/script.php'I get

This page isn&#8217;t working
localhost is currently unable to handle this request.
HTTP ERROR 500

---

### Post by dragonfly41 on 2018-07-21
Drop this script into /var/www/html/

phpinfo.php ..
```

<?php
echo phpinfo();
?>

```

and run [http://localhost/phpinfo.php](http://localhost/phpinfo.php)

Check also that your scripts permissions are owned by www-data.

---

### Post by mIk3_08 on 2018-07-21
> **zkab said:**
> 1) [http://localhost](http://localhost) gives me - Apache2 Ubuntu Default Page
2) $ phpinfo() gives me a prompt > 
3) When I moved the script to /var/www/html and made it executable and run 'http://localhost/script.php'I get

This page isn’t working
localhost is currently unable to handle this request.
HTTP ERROR 500


what is in your script.php? if you are about to move the file  /var/www/script.php then this will run as a php page under [http://localhost](http://localhost) but
If you get 

This page isn’t working
localhost is currently unable to handle this request.
HTTP ERROR 500

After running [http://localhost](http://localhost)
Then there is something wrong with your script.php.

---

### Post by mIk3_08 on 2018-07-21
Here are some instructions of successful installation of LAMP Server on Ubuntu. [Click Here]("https://howtoubuntu.org/how-to-install-lamp-on-ubuntu#install-php")

---

### Post by zkab on 2018-07-21
The phpinfo.php run just fine ... my script is dependent of files in a sub-directory ... so how do I change it will execute in that directory ... can I make a link in /var/www/html/ ?

---

### Post by dragonfly41 on 2018-07-21
Without having further information about your script why not place it in /var/www/html/ and then edit your script to refer to the absolute path of your sub-directory?

Other than that, create a virtualhost to point to your document root.

---

### Post by mIk3_08 on 2018-07-22
> **zkab said:**
> The phpinfo.php run just fine ... my script is dependent of files in a sub-directory ... so how do I change it will execute in that directory ... can I make a link in /var/www/html/ ?

yes, you can create here;
/var/www/html/newdir

and put your script.php inside newdir

and try to run link below in your browser;
[http://localhost/newdir](http://localhost/newdir)

---

### Post by zkab on 2018-07-22
OK - I copied my subdir - Downloads - to /var/www/html/ so now I have
/var/www/html$ ls -l
total 28
drwxr-xr-x 9 root root 12288 jul 22 11:38 Downloads

where all my files and scripts are.
When I run [http://localhost/Downloads/](http://localhost/Downloads/) I get:

Index of /Downloads
	Name	Last modified	Size	Description
[PARENTDIR]	Parent Directory	 	-	 	 
[ ? ]	addnewacct.php	2018-07-22 11:38	6.1K	 
... all files are listed here ...

When I click at the script in the list then I get:
This page isn’t working
localhost is currently unable to handle this request.
HTTP ERROR 500

---

### Post by zkab on 2018-07-22
I forgot to metion that I have LAMP installed also ...

---

### Post by mIk3_08 on 2018-07-22
> **zkab said:**
> OK - I copied my subdir - Downloads - to /var/www/html/ so now I have
/var/www/html$ ls -l
total 28
drwxr-xr-x 9 root root 12288 jul 22 11:38 Downloads

where all my files and scripts are.
When I run [http://localhost/Downloads/](http://localhost/Downloads/) I get:

Index of /Downloads
    Name    Last modified    Size    Description
[PARENTDIR]    Parent Directory         -          
[ ? ]    addnewacct.php    2018-07-22 11:38    6.1K     
... all files are listed here ...

When I click at the script in the list then I get:
This page isn’t working
localhost is currently unable to handle this request.
HTTP ERROR 500


try to check your php script maybe you have made a little silly mistakes. try to recheck again line by line. php is a flying code maybe it will not run directly by page maybe it will only run when its called via code. or you can try running via index.

---

### Post by zkab on 2018-07-22
OK - thanks for your support ... I will check the script

---

### Post by mIk3_08 on 2018-07-23
sample of call php
```
<?php get_filename(); ?>
```
[PHP]<?php get_filename(); ?>[/PHP]
filename should be the one that is being called.

---

### Post by zkab on 2018-07-23
Ok

---

