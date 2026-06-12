---
title: "php installed but not working in Apache"
date: 2024-06-01
forum: General Help
---

### Post by garyed on 2024-06-01
It looks like php is installed & active but I can't get my Apache server to work with a php file.
Results of```
php -v
``` 
PHP 8.3.7 (cli) (built: May 23 2024 12:36:54) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.3.7, Copyright (c) Zend Technologies
    with Zend OPcache v8.3.7, Copyright (c), by Zend Technologies
If I run ```
php -1
``` it will give me the info just like phpinfo() would normally do on a web page.
Any ideas of what I do to get it working?

---

### Post by dragonfly41 on 2024-06-01
What if you try PHP dev server?   -S option

[https://www.php.net/manual/en/features.commandline.webserver.php](https://www.php.net/manual/en/features.commandline.webserver.php)

---

### Post by garyed on 2024-06-01
> **dragonfly41 said:**
> What if you try PHP dev server?   -S option

[https://www.php.net/manual/en/features.commandline.webserver.php](https://www.php.net/manual/en/features.commandline.webserver.php)

Not sure what command you want me to execute but everything I tried was invalid.

---

### Post by yancek on 2024-06-01
>   I can't get my Apache server to work with a php file.


What does that mean 'to work'??  What exactly happens when you try to access a php page from a web browser?  Is that the actual problem?  Which Ubuntu release are you using?  Is this a new setup, meaning did php ever work on the system?  If you put the code below in a file in /var/www/html and save as a php file, does it output anything in a browser?

> <?php phpinfo(); ?> 

---

### Post by garyed on 2024-06-01
> **yancek said:**
> What does that mean 'to work'??  What exactly happens when you try to access a php page from a web browser?  Is that the actual problem?  Which Ubuntu release are you using?  Is this a new setup, meaning did php ever work on the system?

When I access a php page on my server from my web browser all the code just comes up as a text file. 
That is the actual problem. It's as though Apache does not know that I have php installed. 
I tried upgrading from Ubuntu 22.04 to 24.04 & it didn't fix the problem. 
I can't remember exactly when my problems started but I had been running Apache for years with no problems. 
I think it started a little while ago after running an update but I can't be certain. 
Originally I couldn't even access any pages on my Apache server so I tried to uniunstall & then reinstall Apache. 
Now Apache works but I can't get it to interpret php web pages correctly.
I'm assuming I'm either missing a dependency or some setting in my system.

---

### Post by garyed on 2024-06-01
Well I'm not sure what happened but I just got back home & turned my computer on & now everything is working OK. 
Php files are being processed properly on my server & no more displaying the code in text form.

---

