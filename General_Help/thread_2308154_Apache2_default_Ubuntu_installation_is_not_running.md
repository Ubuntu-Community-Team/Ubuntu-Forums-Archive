---
title: "Apache2 default Ubuntu installation is not running php files (permissions problem?)"
date: 2015-12-31
forum: General Help
---

### Post by jimspiti on 2015-12-31
I just install Ubuntu 14.04 and i run apt-get update and apt-get upgrade.

I install then the php and i have this:

> pamamolf@ubuntu:~$ apache2 -v
Server version: Apache/2.4.7 (Ubuntu)
Server built:   Oct 14 2015 14:20:21

> pamamolf@ubuntu:~$ php -v
PHP 5.5.9-1ubuntu4.14 (cli) (built: Oct 28 2015 01:34:46) 
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.5.0, Copyright (c) 1998-2014 Zend Technologies
    with Zend OPcache v7.0.3, Copyright (c) 1999-2014, by Zend Technologies

Both seems ok ...

When i browse with firefox on : 192.168.1.100 or localhost or 127.0.0.1 the default html is coming up without any issues.

> Apache2 Ubuntu Default Page

Then i git clone a php project in /var/www/html/folderx/index.php

When i browse to this file: 192.168.1.100/folderx/index.php i am getting a blank page :(

Then i create a simple php file Hello word sample and add it at /var/www/html/ and then try again with 192.168.1.100/index.php but nothing i got again a blank page :(

Any ideas?

Thank you and a happy new year to all !

---

### Post by Habitual on 2015-12-31
Is php5-mysql installed?

---

### Post by sandyd on 2015-12-31
What does
```

sudo apt-get install php5-cli
php /var/www/html/folderx/index.php
```

output?

---

