---
title: "PHP doesn;t work"
date: 2008-05-15
forum: General Help
---

### Post by Leahy on 2008-05-15
I have installed apache, it works, but php will not..(the script is displayed in browser)

When I enter the following, the response makes me believe it is installed ????  help !!

$ which php
/usr/local/bin/php


$ php -v
PHP 5.2.6 (cli) (built: May 13 2008 16:54:37)
Copyright (c) 1997-2008 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1997-2008 Zend Technologies

---

### Post by cpetercarter on 2008-05-15
First thing to check is that the script you are trying to run has a .php extension.

---

### Post by fyo on 2008-05-15
> **Leahy said:**
> I have installed apache, it works, but php will 
$ which php
/usr/local/bin/php


$ php -v
PHP 5.2.6 (cli) (built: May 13 2008 16:54:37)
Copyright (c) 1997-2008 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1997-2008 Zend Technologies

That's completely irrelevant. You don't need that installed.

What's important is that APACHE has it's php module installed (OK, there are other ways, but that's the "normal" way).

If you're using a package manager, search for php and install the appropriate apache module, e.g. libapache2-mod-php5.

Hope that helps ;-)

(I don't have the php5 package installed, but the one above... which is exactly what I need for my web server to work with php).

---

