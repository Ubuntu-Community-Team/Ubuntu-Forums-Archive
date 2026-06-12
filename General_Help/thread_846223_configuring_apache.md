---
title: "configuring apache"
date: 2008-07-01
forum: General Help
---

### Post by hirohitosan on 2008-07-01
I installed apache on my system
Which is the configuration file?
/etc/apache2/apache2.conf or /etc/apache2/httpd.conf?

thanks

---

### Post by cmnorton on 2008-07-01
This is an interesting question. I looked on my system and httpd.conf is 0 length, so apache2.conf appears to be "the" config file.

---

### Post by fragos on 2008-07-01
httpd.conf is for your changes, it's called by apache2.conf.

---

