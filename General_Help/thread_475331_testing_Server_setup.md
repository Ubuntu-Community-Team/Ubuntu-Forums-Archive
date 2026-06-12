---
title: "testing Server setup"
date: 2007-06-16
forum: General Help
---

### Post by malfist on 2007-06-16
I want to set up a LAMP for test on my computer (post-ubuntu installation). I've done it in windows but I don't really know how to set it up in linux. Can anyone point me in the right direction? It's just a one user test server for testing updates before they become live on a hobby webpage.

Thanks,
Malfist


For anyone who doesn't know, a LAMP is a Linux Apache MySQL PHP server. (On windows it's a WAMP)

---

### Post by zvacet on 2007-06-16
**synaptic<edit>mark package by task**

[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP")

---

### Post by malfist on 2007-06-16
Thank you, but I'm getting an error message on trying to load index.php in /var/www/
> 

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
How can I fix this? I installed php-pear after it gave me that error and restarted apache but that didn't help.

---

### Post by malfist on 2007-06-16
Fixed, needed to edit apache.conf and change User and Group to me.

---

