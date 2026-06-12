---
title: "apache2 and php: httpd not running"
date: 2007-09-21
forum: General Help
---

### Post by gordonsowner on 2007-09-21
Hi,

I am trying to get apache2 to recognize php pages.  I can serve up a static .html page in a given directory through 'http://localhost/...', but not a .php page in the same directory.

I've installed everything according to: [http://www.howtoforge.com/perfect_setup_ubuntu704_p6](http://www.howtoforge.com/perfect_setup_ubuntu704_p6), but when i issue the following, i get the following error message:
```

xxxx@ubuntu-home:/etc/init.d$ sudo apache2 -k restart
httpd not running, trying to start

```

But httpd doesn't start -- as i can tell by grepping the processes... any ideas?

thanks,

UPDATE:

I looked at the error log and found:

```
[Fri Sep 21 15:34:01 2007] [error] (2)No such file or directory: Cannot create SSLMutex with file `/var/run/apache2/ssl_mutex'
Configuration Failed
```

I don't have a /var/run/apache2 directory...

UPDATE 2:
I ran the following and now my .php file will render:

```

sudo a2dismod ssl
/etc/init.d/apache2 force-reload
sudo apache2 -k restart

```

Any ideas what the problem is?

---

### Post by andrewsben on 2007-12-26
Gordonsowner:

I think that I had the same problem as you and discovered the way to fix it.  Basically within /etc/default/apache2 the variable NO_START was set to 1, change this to 0 and then /etc/init.d/apache2 will create the /var/run/apache2 directory and be able to start.  Hope this helps.

Ben

---

