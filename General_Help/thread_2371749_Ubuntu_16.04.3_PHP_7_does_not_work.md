---
title: "Ubuntu 16.04.3: PHP 7 does not work"
date: 2017-09-18
forum: General Help
---

### Post by planteg2 on 2017-09-18
Hi all,

I just installed Ubuntu 16.04.3 (64-bit) in a Virtual Machine (VMWare Player 12). I want to install LAMP for tests purposes. Apache2, MySQL and PHP are installed. Thing is PHP doesn't work.

Fisrt installation was done with [FONT=courier new]sudo apt-get install php[/FONT]. Then I installed phpmyadmin with [FONT=courier new]sudo apt-get install phpmyadmin[/FONT]. phpmyadmin didn't work.

So I googled and found this [https://askubuntu.com/questions/760907/upgrade-to-16-04-php7-not-working-in-browser](https://askubuntu.com/questions/760907/upgrade-to-16-04-php7-not-working-in-browser) In there one tells to install PHP this way [FONT=courier new]sudo apt-get install php7.0-mysql php7.0-curl php7.0-json php7.0-cgi  php7.0 libapache2-mod-php7.0[/FONT]. But that didn't help.

When I run [FONT=courier new]php -v[/FONT], i get this:
> PHP 7.0.22-0ubuntu0.16.04.1 (cli) ( NTS )
Copyright (c) 1997-2017 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2017 Zend Technologies
    with Zend OPcache v7.0.22-0ubuntu0.16.04.1, Copyright (c) 1999-2017, by Zend Technologies

which seems right.

When I type localhost/phpmyadmin I get the code instead of the actual page. If I try to open phpinfo.php in Firefox, same thing happens, I get:
```
disable(); /** * Displays PHP information */ if ($GLOBALS['cfg']['ShowPhpInfo']) { phpinfo(); }
```

Looks like PHP is not running at all. What's going on ? How can't I have PHP working ?

Thanks

Gilles Plante

---

### Post by dragonfly41 on 2017-09-18
Is Apache2 server running .. this command will test ...

```
sudo systemctl status apache2
```

---

### Post by planteg2 on 2017-09-18
Hi dragonfly41,

tried your command, everything is fine except that it "could not reliably determine the server's fully qualified domain name". That's Ok with me.

In the mean time I found out that the issue could be caused by short tags not being enabled. In fact they were not enable. I enabled them and was able to load and run phpmyadmin.

Regarding phpinfo, I created a .php file in /var/www/html that calls phpinfo() and that works fine now.

---

