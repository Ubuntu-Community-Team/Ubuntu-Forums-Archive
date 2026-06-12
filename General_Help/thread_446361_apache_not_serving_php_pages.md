---
title: "apache not serving php pages"
date: 2007-05-16
forum: General Help
---

### Post by ivantxu on 2007-05-16
**This post could be related to an Ubuntu bug filed at**: 106707 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi everyone, I know this is a common question, but recent similar posts have not been much help, so here it goes again.  Some time ago I used to have a working php in apache, which I mainly used for a local installation of mediawiki.  However, that seems to be broken now; I've only realized after upgrading to feisty, but it may have been going on for a while before.  If I try execute a php file (eg [http://localhost/mediawiki/](http://localhost/mediawiki/)), the browser only gives me the option tod download the page as text ("You have chosen to open [blank] which is a: PHTML file.  What should Firefox do with this page?").

I've tried purging all relevant packages (mediawiki, apache2, php5, php5-mysql, etc.) and reinstalling, to no avail.  All relevant config files seem to be in place (/etc/apache2/mods-enabled/php5.conf|load), and the only thing the apache's error.log shows is

```
Apache/2.2.3 (Ubuntu) PHP/5.2.1 configured -- resuming normal operations
```

The issue might be related to the bug referenced above, the closest I found in launchpad.

Any ideas?  Thanks

---

### Post by calenti on 2007-05-23
I am having this issue as well after upgrading my server from Dapper to Feisty. PHP files are being delivered to the processor instead of being processed.

FWIW, I can run PHP from the command line

```

/etc/apache2$ php -version
PHP 5.2.1 (cli) (built: May 22 2007 19:05:44)
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

```


and works from the command line:

```

php testphp.php
phpinfo()
PHP Version => 5.2.1

System => Linux em366is 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686
Build Date => May 22 2007 19:03:51
Server API => Command Line Interface
Virtual Directory Support => disabled
Configuration File (php.ini) Path => /etc/php5/cli/php.ini
Scan this dir for additional .ini files => /etc/php5/cli/conf.d
additional .ini files parsed => /etc/php5/cli/conf.d/gd.ini,
/etc/php5/cli/conf.d/mysql.ini,
/etc/php5/cli/conf.d/mysqli.ini,
/etc/php5/cli/conf.d/pdo.ini,
/etc/php5/cli/conf.d/pdo_mysql.ini,
/etc/php5/cli/conf.d/xsl.ini

PHP API => 20041225
PHP Extension => 20060613
Zend Extension => 220060519
Debug Build => no

```

...you get the idea.

My thread is [http://ubuntuforums.org/showthread.php?t=452956](http://ubuntuforums.org/showthread.php?t=452956), if you see anything or want to share ideas leave a message.

---

### Post by shravan on 2007-06-29
this might be too late and you might have figured out how to fix it.

in the following link, they tell you how to install the LAMP

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


in the troubleshooting section, they mention that 

Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. [COLOR="Red"]**Be sure to clear your browser's cache before testing your site again**[/COLOR].

After following all the steps, 
The one highlighted at the end is very important. It means goto to Tools in your firefox 2.0, click on "clear private data", check cache and say clear. It worked only after i did that. 

hope this helps

---

### Post by ivantxu on 2007-06-30
It got fixed in the radical way: reinstalling feisty, I could find no other solution and I really needed a working mediawiki...

Thanks anyway

---

### Post by IncomingFire on 2007-11-05
Sorry to bump an old thread but this is the first result for the google search "apache not serving php +ubuntu", as the search function in the forums wasn't helping.

In any case, what I found I had to do after updating was actually purge the libapache2-mod-php5 package and reinstall.

```

sudo apt-get purge libapache2-mod-php5
sudo apt-get install libapache2-mod-php5

```

Then clear my browser's cache and revisit the page.

This happened after upgrading to 7.10 that this seemed to get broken.

---

### Post by amorangi on 2007-12-11
Thanks people, I reinstalled all the apache2 and php5 stuff to no avail - the "sudo a2enmod php5" did the trick though. Much appreciated.

---

