---
title: "Apache2 - port:80"
date: 2008-01-09
forum: General Help
---

### Post by tmlingam on 2008-01-09
hi

am new to Ubuntu, and i tried to install apache2, i was successful and apache2 was working fine. but in due process of installing other packages somehow the Apache got corrupted and now its not working.

when i try to restart

sudo /etc/init.d/apache2 restart

* Restarting web server apache2 
httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs [fail]

i don't know what the problem is.

when i try to check the port

sudo lsof -i:80

COMMAND PID USER FD TYPE DEVICE SIZE NODE NAME
nginx 5059 root 6u IPv4 16605 TCP *:www (LISTEN)
nginx 5060 www-data 6u IPv4 16605 TCP *:www (LISTEN)

someone help me plss..

---

### Post by chippy99 on 2008-01-09
You have the NGINX webserver running and it has grabbed port 80. Stop NGINX and then try restarting Apache.

---

