---
title: "Installing dcl"
date: 2007-07-03
forum: General Help
---

### Post by StonePiano on 2007-07-03
Has anyone installed dcl (Double Choco Latte) on Ubuntu?
[http://dcl.sourceforge.net/]("http://dcl.sourceforge.net/")
dcl is a time-tracking, call-tracking, basic project management package.

I installed it from the synaptic repositories.  The main php files went into:
```
/usr/share/dcl/www/
```

I created a symbolic link:
```
ln -s /usr/share/dcl/www /var/www/dcl
```

Apache is running for other applications.  But when I browse:
[http://localhost/dcl/](http://localhost/dcl/)

I get:
-----------------------
Warning: include({VAL_dcl_root}{VAL_dbType}.php) [function.include]: failed to open stream: No such file or directory in /etc/dcl/config.php on line 108

Warning: include() [function.include]: Failed opening '{VAL_dcl_root}{VAL_dbType}.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /etc/dcl/config.php on line 108

Fatal error: Class 'dclDB' not found in /usr/share/dcl/www/inc/class.dbConfig.inc.php on line 25

-----------------------

The setup instructions refer to a dcl/setup directory which was not installed with dcl (as far as I can find).
[URL="http://dcl.sourceforge.net/wiki/index.php/Installation_Guide#Setup"]
http://dcl.sourceforge.net/wiki/index.php/Installation_Guide#Setup[/URL]

Has anyone done this successfully?

Many thanks,
StonePiano

---

