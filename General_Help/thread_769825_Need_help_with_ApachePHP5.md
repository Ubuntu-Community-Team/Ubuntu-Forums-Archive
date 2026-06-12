---
title: "Need help with Apache/PHP5"
date: 2008-04-26
forum: General Help
---

### Post by fred!head on 2008-04-26
Hi,

Quite possibly this is a stupid newbie error but if anyone can help me work through possible solutions, I'd appreciate it.

I have Ubuntu Gutsy, Apache 2, PHP5, MySQL, phpMyAdmin installed. Using Webmin, everything appears fine. When I call up a PHP page, however, I get the PHP code instead of the server output. Same for when I call up phpMyAdmin. Webmin tells me Apache runs fine, the Apache PHP5 module is enabled, the PHP configuration file is fine.

Any ideas how to debug this sort of issue? Thanks!

Tim

P.S. I accidentally posted this first on the Ubuntu Installtion forum. If a moderator could delete that post, I'd be grateful.

---

### Post by rgutierrez on 2008-04-26
This is just off the top of my head, but I think you need to configure apache to render php files using AddType. Actually, a quick google of "apache displaying php code" returns this:

[http://www.daniweb.com/forums/thread26079.html](http://www.daniweb.com/forums/thread26079.html)

Basically, the post says to be sure the AddType statement is in the correct location. Read it for details. Hope that helps.

---

### Post by Skipster on 2008-04-26
Well it's hard to say. but it's likley that you have an issue with your httpd.conf file.

do you have something like 
```
AddType application/x-httpd-php php
```
in there?

---

### Post by fred!head on 2008-04-26
It turns out to be a GUI error, as in Gross User Incompetence. In my /etc/apache2/mods-available/php5.conf file, the AddTypes were commented out. I've looked at that file a dozen times today and never noticed, probably because there's only 4 lines and it looks okay until you start "reading" each line.

So now I have phpMyAdmin running and I have to figure out why it won't work with my virtual server passwords set up with Webmin. But I figure that's a config issue.

Thanks for your prompt help! Sorry it was a stupid user problem.

Tim

---

### Post by cmnorton on 2008-04-28
> **Skipster said:**
> Well it's hard to say. but it's likley that you have an issue with your httpd.conf file.

do you have something like 
```
AddType application/x-httpd-php php
```in there?

Edit Begin:
-------------------------------------------------------------------------------
Everything was configured. I had to make index.php the primary file. 

Edit End:
--------------------------------------------------------------------------------

I have determined the following directives are in in /etc/apache2.conf.

I have PHP5 installed, and the library is being loaded from apache2.conf

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

I cannot get this index.html to run phpinfo. The index.html is in /var/www

<html>
<title>Test index.html page.</title>
<body>
hello
<?php
phpinfo();
?>
</body>
</html>

What do I need to configure? temp.php 

<?php
phpinfo();
?>

works just fine from php -f temp.php

There are no errors or anything else unusual in the logs.

---

