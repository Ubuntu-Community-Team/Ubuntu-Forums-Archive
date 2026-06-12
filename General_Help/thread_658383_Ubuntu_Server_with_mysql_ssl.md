---
title: "Ubuntu Server with mysql ssl"
date: 2008-01-04
forum: General Help
---

### Post by Blastnsmash on 2008-01-04
I was wondering if someone could help me setup ssl with mysql on ubuntu server.

I have mysql installed and running. All the GUI tools work fine with it, here is the version info of mysql: 

5.0.45- Debian_lubuntu3.1-log Debian etch distro. Currently, ssl is disabled.

I've looked over the mysql docks but can't seem to get them working. I've created the certificates for the client, server and ca but any commands I give to mysqld end up in error, something about it doesn't have permissions to do stuff.

Do I just set a config file to point to the certificates? Tutorials or advice would be greatly appreciated.

---

### Post by mtuller on 2008-01-25
Maybe this will help you. [http://dev.mysql.com/doc/refman/5.0/en/secure-using-ssl.html](http://dev.mysql.com/doc/refman/5.0/en/secure-using-ssl.html)

---

