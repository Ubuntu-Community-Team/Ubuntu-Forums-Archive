---
title: "Apache stoped working after installing PHP"
date: 2012-10-28
forum: General Help
---

### Post by skinney6 on 2012-10-28
i installed apache2 "sudo apt-get install apache2"
I saw the "it works" page after i changed the ports.conf listen to 127.0.0.1:80
then
I installed php per this page...
except for the "sudo apt-get install apache2" cuz apache is already installed
[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)
now i can't see the "it works" page

i uninstalled everything i saw when running "dpkg --list|grep -e httpd -e apache -e mysql -e php" i removed them using "apt-get autoremove"

i installed LAMP from the tasksel menu but it still doesn't work
i did notice that my ports.conf file is the same cuz it still has the change i made to "listen"

---

### Post by kanikilu on 2012-11-02
What do you get when you try to access the localhost?

Is apache running?

```
sudo service apache2 status
```

What address and port is it listening on?

```
sudo netstat -tulpn | grep apache2
```

Have you tested the config?

```
sudo apachectl configtest
```

Anything in the error log?

```
cat /var/log/apache2/error.log | tail
```

As a last resort, you may want to try purging everything (not just remove), and that should remove configuration files as well. And then try reinstalling...?

---

### Post by skinney6 on 2012-11-02
sorry for the delay, i thought i'd get an email if someone replied.

sudo service apache2 status
**Apache2 is running (pid 1202).**
~$ sudo netstat -tulpn | grep apache2
**tcp        0      0 127.0.0.1:80            0.0.0.0:*   **            **LISTEN      1202/apache2**
~$ sudo apachectl configtest
**Syntax OK**
 cat /var/log/apache2/error.log | tail
[Thu Nov 01 09:53:25 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 01 10:03:43 2012] [notice] caught SIGTERM, shutting down
[Thu Nov 01 10:03:44 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 01 10:08:18 2012] [notice] Graceful restart requested, doing restart
[Thu Nov 01 10:08:19 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 01 10:09:17 2012] [notice] Graceful restart requested, doing restart
[Thu Nov 01 10:09:17 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 01 10:09:32 2012] [notice] caught SIGTERM, shutting down
[Thu Nov 01 10:09:34 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 01 18:40:34 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations

---

### Post by kanikilu on 2012-11-02
So what's the error you get when trying to bring up the default page ([http://localhost/)?](http://localhost/)?)

I know you said it was working with that change in the ports.conf file, but that's the only difference between my (working) setup, and yours. Maybe change it back to ```
NameVirtualHost *:80
``` and restart the service...?

---

### Post by skinney6 on 2012-11-02
Oops! Google Chrome could not connect to localhost

this is my ports.conf

NameVirtualHost *:80
Listen 127.0.0.1:80

i changed Listen from :80 to 127.0.0.1:80

i'll change listen back to 80 & restart

- didn't work

---

### Post by skinney6 on 2012-11-08
purged & reinstalled phpmyadmin had no affect
i just reinstalled ubuntu server. i didnt format. i just unstalled right over the old sys keeping lvm
installed ssh. when everything was complete i 'tasksel' and installed lamp changed the configs to loopback and servername localhost still can't see index.html.
installed phpmyadmin nothing
i dont know what's going on...my dsl router has a firewall but i'm opperating inside of it and apache worked before between these two computers.
i dont know what else i can do

---

