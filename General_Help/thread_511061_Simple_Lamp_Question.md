---
title: "Simple Lamp Question"
date: 2007-07-27
forum: General Help
---

### Post by netvampire on 2007-07-27
I am new to anything to do with php. I appreciate the help.

Essentailly I am tryign to set up kplaylist. I installed kubuntu using the server option on the installation disk. I enabled the lamp server to be installed.

I am now in the kubuntu desktop, and i have downlaoded kplaylist. The installation instructiosn say to place the kplaylist file in the 'htdocs' folder. I am assuming it is this folder that gets loaded by apache with php support. Well with my installation, I can not find this folder. I did a 'locate' search, but still no luck.

Soi guess my question is, what directory is it that people place php files into to have them used with the apache2 +php web server. thanks:)

---

### Post by amac777 on 2007-07-27
If you already have both Apache and PHP installed then putting the php files in any directory under the websever should allow them to be executed.

For example, on my computer, the webserver directory is:

/var/www

You could put php files in there and then access them by going to this url in firefox:

[http://localhost](http://localhost)

Let me know if that answers your question.

EDIT: I don't actually know what kplaylist is so my help might not be exactly useful. I just run lots of php files on my computer and I put them all under /var/www.

---

### Post by netvampire on 2007-07-27
thanks for the response.

I have indeed found the folder var/www.

KPlaylist uses  a lamp installation to allow a person to stream there music through a web browser. As part of the installation instructiosn I am suppose to deploy a *.php file in a web browser. 

I believe to have lamp installed because i did the server installation. I looked in the Adept Manager and it says i have apache2, php5-common, php5-mysql, libapache2-mod-php5 installed.

Now when i placed the kplaylist *.php file in the /var/www/kplaylist/ directory, and restart apache2, i get this error 

```

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/kplaylist/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0


```

does anyone know what the problem could be..... Thanks :0

---

### Post by netvampire on 2007-07-27
i am sure php is configured fine because i just deplyed a file phpinfo.php 
with this content 

```

<?php

echo phpinfo();

?>

```
So i am assuming the problem lies with kplaylist.

---

### Post by zanglang on 2007-07-27
Try
> sudo chown -R www-data:www-data /var/www/kplaylist
and see if that works? Your Apache probably didn't have read permissions from the .php scripts.

---

### Post by netvampire on 2007-07-27
thanks. 

setting the ownership worked great.

---

