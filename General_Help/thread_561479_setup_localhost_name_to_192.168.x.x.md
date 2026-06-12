---
title: "setup localhost name to 192.168.x.x"
date: 2007-09-27
forum: General Help
---

### Post by Rick Z on 2007-09-27
Does anyone know how to change the name to where when type in [https://mylinuxbox](https://mylinuxbox) it will display the default [https://localhost/](https://localhost/) or [http://127.0.0.1](http://127.0.0.1) info?

I frequently access to my linux box with another pc via webmin([https://192.168.1.x:10000](https://192.168.1.x:10000)) or ssh(ssh username@192.168.1.x).  

I am developing a database using mysql+php, but every time when I want to access to the [https://localhost](https://localhost) from another computer I would have to enter [http://192.168.1.x](http://192.168.1.x).  Is there another way to setup a name such as [http://mylinuxbox?](http://mylinuxbox?)

Thanks.

---

### Post by dcstar on 2007-09-28
> **Rick Z said:**
> Does anyone know how to change the name to where when type in [https://mylinuxbox](https://mylinuxbox) it will display the default [https://localhost/](https://localhost/) or [http://127.0.0.1](http://127.0.0.1) info?

I frequently access to my linux box with another pc via webmin([https://192.168.1.x:10000](https://192.168.1.x:10000)) or ssh(ssh username@192.168.1.x).  

I am developing a database using mysql+php, but every time when I want to access to the [https://localhost](https://localhost) from another computer I would have to enter [http://192.168.1.x](http://192.168.1.x).  Is there another way to setup a name such as [http://mylinuxbox?](http://mylinuxbox?)

Thanks.

Add the entry to your hosts file:

System-Administration-Network-Hosts

---

### Post by Rick Z on 2007-09-28
Hi David,

Thank you for your respond.  I will give that a try on one of my linux box that has x-server installed.  How do we change/add that on a linux box that doesn't have x-server setup?  Under what Directory could I change the hostname/computer name?  Is this under /etc/hosts?

Thanks!!

---

