---
title: "Apache PHP MySQL for testing"
date: 2007-08-12
forum: General Help
---

### Post by saxbald on 2007-08-12
Hi there!

I'd like to install Apache/PHP/MySQL on my Ubuntu Feisty and use it to test my PHP-scripts. 
Is it possible to do that in a simple way without the Internet having access to my computer? I don't want to run a webserver. I want to keep it secure from the internet.

Kind regards!

Saxbald

---

### Post by jamvegan on 2007-08-16
The [Ubuntu Server Guide]("https://help.ubuntu.com/7.04/server/C/") has lots of good information about how to install the software you want.

After installing, you can run /usr/bin/mysql_secure_installation ([MySQL Documentation]("http://dev.mysql.com/doc/refman/5.0/en/mysql-secure-installation.html")) to secure MySQL.

To tell Apache not to respond to requests over the network, edit /etc/apache2/apache2.conf and add the following lines:
```
<Location />
Order deny,allow
Deny from all
Allow from localhost
</Location>

```

---

### Post by saxbald on 2007-09-18
thank you for your help

i'll try that right now

saxbald

---

