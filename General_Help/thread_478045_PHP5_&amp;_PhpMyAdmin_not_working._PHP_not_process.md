---
title: "PHP5 &amp; PhpMyAdmin not working. PHP not processing?"
date: 2007-06-18
forum: General Help
---

### Post by dpollen on 2007-06-18
Hi people!,

I have been trying to install PHP5, apache2 and MySQL for a testing server.

I have installed:
[B]PhpMyAdmin 
MySql-Server-5.0
Apache2.2-common
PHP-5.0
& all dependencies.[/B]

When I go into **Apache2-default** I get the message: "IT WORKS!"
However, when I try and go to the **phpmyadmin** folder, it just prompts to download a **.phtml** file.

I tested a
[PHP]<?php echo php_info()  ?>[/PHP]
page and I simply got a file containing the code.

I reinstalled the packages, restarted the machine, cleared firefox cache... same thing.

**How do I get php pages to process???**

:guitar:

Thanks :)

---

### Post by dpollen on 2007-06-18
**When I restart Apache I get a weird message too:**
```
brett@The Little Ubu:~$ sudo apache2ctl restart
Password:
apache2: apr_sockaddr_info_get() failed for The Little Ubu
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
```



**my etc/hosts file**
```

127.0.0.1 localhost
127.0.1.1 brett-laptop-ubuntu.commerce

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcas
tprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.1 Wireless Router

```

---

### Post by dpollen on 2007-06-19
? :-\"

---

### Post by bazzer on 2007-06-19
Found on a quick search how to get rid of that error when starting Apache2:
[INDENT]Troubleshooting

If you get this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

then edit gksudo gedit /etc/apache2/apache2.conf and add ServerName localhost at the end of the file [/INDENT]
[https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031")

However, I'm experiencing exactly the same right now and wanting a fix!! If I find it I'll let you know! ;)

EDIT: Found it....
```
sudo gedit /etc/apache2/mods-available/php5.conf
```
and do something like this:
[INDENT]AddType application/x-httpd-php .htm .html .php .phtml .php3[/INDENT]

---

### Post by cmcginty on 2008-04-13
[COLOR="Red"][SIZE="3"]**!! Make Sure To Clear Your Browser Cache After Restarting Apache !!**[/SIZE][/COLOR]

---

