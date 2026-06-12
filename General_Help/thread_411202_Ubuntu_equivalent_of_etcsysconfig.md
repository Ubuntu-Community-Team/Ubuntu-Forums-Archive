---
title: "Ubuntu equivalent of /etc/sysconfig"
date: 2007-04-16
forum: General Help
---

### Post by x1a4 on 2007-04-16
Hi,

Many other GNU/Linux distributions have important configuration files in /etc/sysconfig.  Is there a Ubuntu equivalent?

Thank you.

---

### Post by earobinson on 2007-04-16
Um I think that they could be all over the place, like I know for example init is often in sysconfig, but in ubuntu we have init.d in /etc/

Anything you where looking for!

and Hello fellow canadian!

---

### Post by x1a4 on 2007-04-16
> **earobinson said:**
> Anything you where looking for!
/etc/sysconfig/network
/etc/sysconfig/static-routes
/etc/sysconfig/routed

> and Hello fellow canadian!
Hello to you, eh.  :)

---

### Post by earobinson on 2007-04-17
/etc/sysconfig/network = /etc/network
/etc/sysconfig/static-routes = 
/etc/sysconfig/routed =

(looking into the other 2 now)

---

### Post by earobinson on 2007-04-17
nm all the info seems to be in the network folder!

---

### Post by mesqa on 2008-06-24
Hi, this is my first post in ubuntuforums , The majority of scripts needed to start and stop , manage network interfaces and behaviour are located in /sbin , ifup, ifdown ...
the interface configuration is in the /etc/networ/interfaces file.

To reload the network interface just do /etc/init.d/networking restart.

Hope that will help you.

---

