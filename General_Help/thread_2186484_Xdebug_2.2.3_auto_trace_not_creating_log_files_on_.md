---
title: "Xdebug 2.2.3 auto_trace not creating log files on Ubuntu 12.04 with PHP 5.5.5"
date: 2013-11-07
forum: General Help
---

### Post by tech.judger on 2013-11-07
Issue: 


Xdebug does not create any log files in the specified output dir with the auto_trace setting turned On.


PHP config (on Ubuntu 12.04):

PHP 5.5.5-1+debphp.org~precise+2 (cli) (built: Oct 28 2013 12:57:03) 
Copyright (c) 1997-2013 The PHP Group
Zend Engine v2.5.0, Copyright (c) 1998-2013 Zend Technologies
    with Zend OPcache v7.0.3-dev, Copyright (c) 1999-2013, by Zend Technologies
    with Xdebug v2.2.3, Copyright (c) 2002-2013, by Derick Rethans


Xdebug config (in php.ini):

[XDebug]
zend_extension = /usr/lib/php5/20121212/xdebug.so

xdebug.default_enable = On
xdebug.remote_enable = 1
xdebug.remote_handler = dbgp
xdebug.remote_host = localhost
xdebug.remote_port = 9000
xdebug.remote_autostart = 1
xdebug.remote_log = /var/log/apache2/xdebug/xdebug.log

xdebug.auto_trace = On
xdebug.trace_output_dir = /var/log/apache2/xdebug/
xdebug.profiler_output_dir = /var/log/apache2/xdebug/
xdebug.max_nesting_level = 1000


All these settings are shown by phpinfo() as well.

I've also set writing permissions on the xdebug folder.

---

