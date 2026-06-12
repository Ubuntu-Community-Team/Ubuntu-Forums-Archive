---
title: "need to get rid of cron messages about php warning"
date: 2017-10-30
forum: General Help
---

### Post by marchello_lippi2 on 2017-10-30
Hi all, 

I'm getting messages each 30 minutes like below example. Please advise how do I get rid of them as my webserver works ok and also I have already installed stuff mentioned below. Thx ahead.

```

From: root@local (Cron Daemon)
To: root@local
Subject: Cron <root@local>   [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi
Date: Mon, 30 Oct 2017 19:09:01 +0200


PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/20151012/mysqlnd.so' - /usr/lib/php/20151012/mysqlnd.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/20151012/mysqli.so' - /usr/lib/php/20151012/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/20151012/pdo_mysql.so' - /usr/lib/php/20151012/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0

```

---

### Post by TheFu on 2017-10-31
Seems your php is looking for  mysql in the wrong places?  Why not fix that?

---

### Post by marchello_lippi2 on 2017-10-31
> **TheFu said:**
> Seems your php is looking for  mysql in the wrong places?  Why not fix that?
How do I fix that, any advise pls ?

---

### Post by TheFu on 2017-11-01
I took the error message and put it into google.
[https://stackoverflow.com/questions/5282264/php-warning-php-startup-unable-to-load-dynamic-library](https://stackoverflow.com/questions/5282264/php-warning-php-startup-unable-to-load-dynamic-library) was the first result.

---

### Post by marchello_lippi2 on 2017-11-02
Thx **TheFu**.
 The stackoverflow link above describes the situation in general. 
In my case, I had to look for the module name in /etc/ using grep

> sudo grep -i "pdo_mysql.so" /etc/* -R

Then I edited each found .ini file and commented out module name using semicolon ( ; ) 

> sudo nano /etc/php/7.1/mods-available/pdo_mysql.ini

Now I do not receive those messages with errors anymore.

---

