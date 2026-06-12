---
title: "apache2 won't run PHP files =("
date: 2008-05-18
forum: General Help
---

### Post by Aikon- on 2008-05-18
**[COLOR="Red"]SOLVED[/COLOR]**

I have apache2 installed, along with the libapache2-mod-php5, but PHP files are not executed by the apache server.

I have a simple phpinfo.php file:

```
<?php

phpinfo();

?>

```

saved in Apache's root directory (still /var/www, as default). When I browse to [http://localhost/](http://localhost/), I see that file in the directory listing. When I click on the PHP file (or type the address in explicitly), as in [http://localhost/phpinfo.php](http://localhost/phpinfo.php), Firefox gives me the option to save the file or open it with a program.. it isn't run by Apache.

Any ideas?

Aikon-

---

### Post by wildteen88 on 2008-05-18
Have you restarted Apache? Are you sure the php5 module is enabled?

Run the following come in a terminal
sudo a2enmod php5

That should enable the php5 module in Apache. To restart Apache run:
sudo /etc/init.d/apache2 reload

Retest.

I foound the following [site](http://articles.slicehost.com/ubuntu-hardy) handy for understanding the setup of Apache/PHP on ubuntu (Scroll to the bottom of the page). I know its for setting up a slicehost account but its the same thing for desktop.

---

### Post by Aikon- on 2008-05-18
I ran the following:

```
sarmitage@ophelia:~$ sudo a2enmod php5
[sudo] password for sarmitage: 
Module php5 installed; run /etc/init.d/apache2 force-reload to enable.
sarmitage@ophelia:~$ sudo /etc/init.d/apache2 force-reload
 * Reloading web server config apache2                                   [ OK ] 
sarmitage@ophelia:~$ 
```

and then re-tested. Firefox still tries to open the PHP file instead of having Apache run in.

**Edit:** Note that if I download the file using Firefox, it is served as a ".phtml" file.. opening it in a text editor reveals the initial PHP source.

---

### Post by Aikon- on 2008-05-18
Sigh.. apparently this started working after clearing Firefox's cache ><

---

