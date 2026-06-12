---
title: "small pache problem"
date: 2007-10-14
forum: General Help
---

### Post by Guardian-Mage on 2007-10-14
I get the following error every time I start/stop apache. How can I fix it?

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

---

### Post by thirddeep on 2007-10-14
Edit your /etc/hosts file and put in your sever name.

For example:
```
127.0.0.1       localhost.localdomain localhost
123.1.1.123  bla.bla.com bla
```

Thd.

---

### Post by milosz.galazka on 2007-10-14
Try adding line 
```
ServerName *:80
```

to /etc/apache2/apache2.conf file

---

### Post by Guardian-Mage on 2007-10-14
thanks milosz.galazka, that worked

---

