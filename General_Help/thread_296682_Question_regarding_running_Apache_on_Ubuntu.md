---
title: "Question regarding running Apache on Ubuntu"
date: 2006-11-09
forum: General Help
---

### Post by theicyj on 2006-11-09
I just installed apache, php, ect. on ubuntu. This computer has two network cards, one connected to a lan and the other has direct access to the internet.  Does anyone know if there is a way to force apache to listen only to the nic connected straight to the internet, rather than the one connected to the lan? Everything works great when I have only one card active, but when both are active I keep running into problems.

In other words, I have a computer that has two network cards and I need to set up apache so that is listens to a single network card I specify it to listen to.

(Sorry that this doesn't relate completely to ubuntu, I just couldn't find the answer on google)

---

### Post by Joe_CoT on 2006-11-10
You can change what it listens on by setting its Listen line in your httpd.conf

By default the line should be
```

Listen 80
```
Change it to
```

Listen x.x.x.x:80
```

Where x.x.x.x is your internet ip. then restart apache

---

### Post by theicyj on 2006-11-10
What would I put in place of the x.x.x.x?  I have tried the ip assigned via dhcp from the router. I have one ip address via my ISP.  Other than that each card is assigned, via dhcp, an internal ip address such as 192.168.0.1xx and 192.168.1.1xx.  The card used for the lan is connected to a router (lets call this router 2), which is in turn connected to another router (router 1).  The card that I want apache to listen to is connected straight to router 1.

---

