---
title: "start and stop php"
date: 2007-04-23
forum: General Help
---

### Post by SodiumKPump on 2007-04-23
how do I start and stop PHP from running to I can restart with modified php.ini? thanks

---

### Post by JonnyR on 2007-04-23
Hi There,

Not entirley sure I understand what you mean, but I will give it a go.  PHP is a scriping language which hooks into the Apache Webserver (apache2) in Ubuntu.  In order to "restart" PHP (to load in your new php.ini configuration, for example) you actually need to restart Apache.  You can do this by issuing the following command from the terminal

```
sudo apachectrl restart
```

You will need to enter your root password when requested.

---

