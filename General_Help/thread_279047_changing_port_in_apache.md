---
title: "changing port in apache"
date: 2006-10-17
forum: General Help
---

### Post by mitjab on 2006-10-17
i want to change port from 80 to 8080 in apache but when i look in file /etc/apache2/httpd.conf that i will change it i have only

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so


where i can change it?

thx

---

### Post by Tomosaur on 2006-10-17
I think there's a file called ports.conf.

---

### Post by mtron on 2006-10-17
Http is served on the standard http port 80 and www web caching service
on port 8080. so they are connected. 

why do you wanna change the http port to 8080? 
If you are concerned about port scan scripts & automated attacks use eg port 85.

google is your frind ;) [http://www.apachefriends.org/f/viewtopic.php?t=20376&sid=c8a4f300b07ca4a5148bdffc2c78c36d](http://www.apachefriends.org/f/viewtopic.php?t=20376&sid=c8a4f300b07ca4a5148bdffc2c78c36d)

---

### Post by mitjab on 2006-10-17
becouse my isp block port 80 and i need port 8080.

thx file ports.conf is the right one.

---

### Post by mtron on 2006-10-17
ok, do you use apache1 or apache2 package?

usually debian stores the config files in /etc my apache1 httpd.conf is under 
/etc/apache/httpd.conf

i think for apache 2 it's /etc/apache2/apache2.conf

EDIT: Cool problem solved :cool:

---

