---
title: "phpMyAdmin intallation help"
date: 2005-07-02
forum: General Help
---

### Post by waffull on 2005-07-02
I have apache and php installed, but I can not find phpmyadmin or the php4-mysql mod.  I have the basic ubuntu 5.04 installed.  I have tried aptitude and apt-get, but these packages don't seem to exist. 

Anyone have any ideas?

Thank you...

---

### Post by Majlo on 2005-07-02
[QUOTE=waffull]I have apache and php installed, but I can not find phpmyadmin or the php4-mysql mod.  I have the basic ubuntu 5.04 installed.  I have tried aptitude and apt-get, but these packages don't seem to exist. 

Anyone have any ideas?

Thank you...[/QUOTE]

Hi
Follow this link

[http://www.ubuntuguide.org/#databaseserver](http://www.ubuntuguide.org/#databaseserver)

---

### Post by waffull on 2005-07-02
After adding repositories for apt-get I was able to get phpmyadmin installed through that method.

It installed apache, mysql, php, etc...  in addition to phpmyadim..

The problem I have now is that while I can get the logon page for phpmyadmin, I can not logon.  I presumed the default username would be root with a blank password, but I keep getting this error:

#2002 - Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I'm trying to find out what that means, but if anyone knows it would be a big help.

Thanks,
Marc

---

