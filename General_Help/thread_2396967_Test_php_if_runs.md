---
title: "Test php if runs"
date: 2018-07-23
forum: General Help
---

### Post by hvermesan on 2018-07-23
Hi there, I&#8217;m trying to install wordpress on my server and Icopied all files on my server and the installation file is index.php. I triedto make a test.php file 

```
<?php phpinfo(); ?>
```

to test if php is working but I got this message

> Forbidden
You don'thave permission to access /test.php on this server.
Serverunable to read htaccess file, denying access to be safe


can someone help me with this error?

thenks

---

### Post by SeijiSensei on 2018-07-23
By default, the default document root in Ubuntu is /var/www/html. That directory is owned by "user" www-data. Where is your test.php stored?

---

### Post by hvermesan on 2018-07-24
Hi, the file test.php is in [LEFT][COLOR=#000000][FONT=Ubuntubeta]/var/www/html[/FONT][/COLOR][/LEFT]
-rw-r--r--  user www-data test.php

[COLOR=#222222][FONT="Verdana"]the permissions are correct?[/FONT][/COLOR]

---

### Post by yancek on 2018-07-25
Your owner:group and permissions look correct for that file.  What are the owner:group and permissions on the /var/www directory?
If those permissions are correct it is more likely an error in the WordPress configuration.

---

### Post by Holger_Gehrke on 2018-07-25
You might want to check whether you have a file named '.htaccess' in '/var/www/html' from your Wordpress install and what the permissions on it are. The message you got makes it seem like you do have such a file and that Apache can't read it and blocks all access to the directory to be on the safe side.

Holger

---

### Post by SeijiSensei on 2018-07-26
If you control the server, you shouldn't be using .htaccess files anyway.  Put any directives you might have in .htaccess inside the <Directory> stanza for /var/www/html in the <VirtualHost> container.

---

