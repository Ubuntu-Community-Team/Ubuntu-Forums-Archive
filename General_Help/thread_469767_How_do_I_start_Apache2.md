---
title: "How do I start Apache2"
date: 2007-06-10
forum: General Help
---

### Post by caseyg on 2007-06-10
I just downloaded Apache2 and have been reading up on the apachectl commands although I don't know what directory to locate this file. Do I have to been in the directory to run the apachectl command?

---

### Post by gerscht on 2007-06-10
apache should be started automatically at startup. You can always start/stop/restart it via 
```

sudo /etc/init.d/apache2 [start|stop|restart]

```
apachetl should be located in /usr/sbin/apache2ctl and therefore accessible via
```

sudo apache2ctl [start|stop|restart]

```
I personally prefer the first method (dunno why ;)

---

