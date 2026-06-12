---
title: "PHP headache"
date: 2006-11-26
forum: General Help
---

### Post by roflcopter_1 on 2006-11-26
I'm trying to get php-cli to work correctly. Right now, it works okay, but without mysql support. If I try to connect to a mysql server in a script, it waits for a while, then I get: Can't connect to MySQL server on '(mysql server)' (4) in /home/jmh09/Desktop/sendStats.php on line 19

There isn't a problem with the script, it works elsewhere. I think I have every package imaginable installed, how can I get this to work? Do I need to change something in php.ini? The mysql extension is enabled in there. If it helps, php doesn't work through apache.

---

### Post by roflcopter_1 on 2006-11-26
I just uninstalled and reinstalled everything, and apache works ok, but php doesn't with apache. And mysql still doesn't work with php-cli. Argh...

---

### Post by rickc on 2006-11-26
I'm no PHP/apache/mysql guru, but if you change the .ini file, you have to restart the service for the change to take effect. 
check these posts
[http://www.ubuntuforums.org/showthread.php?t=305521&highlight=mysql](http://www.ubuntuforums.org/showthread.php?t=305521&highlight=mysql)
[http://www.ubuntuforums.org/showthread.php?t=306998&page=2&highlight=mysql](http://www.ubuntuforums.org/showthread.php?t=306998&page=2&highlight=mysql)

---

### Post by procras on 2006-11-26
Easiest way to install and configure php mysql apache is
to follow the outline give in Help->System Documentation->Server Administration->Networking

---

