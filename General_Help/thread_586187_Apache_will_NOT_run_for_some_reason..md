---
title: "Apache will NOT run for some reason."
date: 2007-10-22
forum: General Help
---

### Post by vizitorq on 2007-10-22
I'm using ubuntu Feisty Fawn 7.04 and i've had apache2 running for like a month now with no problems. i rarely shutdown my pc, but last night i did. when i booted it up again today to try and do some development, i found that apache wasn't running!

```

kumi@throne:/etc/apache2 % sudo /etc/init.d/apache2 stop 
 * Stopping web server (apache2)...                                                                                                                          httpd (no pid file) not running
                                                                                                                                                      [ OK ]

kumi@throne:/etc/apache2 % sudo /etc/init.d/apache2 start  
 * Starting web server (apache2)...                                                                                                                          (98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
                                                                                                                                                      [fail]
kumi@throne:/etc/apache2 % ps -e | grep apache
 5350 ?        00:00:00 apache-ssl
 6953 ?        00:00:00 apache-ssl
20359 ?        00:00:00 apache-ssl
20366 ?        00:00:00 apache-ssl
20371 ?        00:00:00 apache-ssl
20374 ?        00:00:00 apache-ssl

kumi@throne:/etc/apache2 % sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

kumi@throne:/etc/apache2 % sudo apache2ctl configtest
Syntax OK

kumi@throne:/etc/apache2 % sudo apache2ctl status
w3m: Can't load http://localhost:80/server-status.
kumi@throne:/etc/apache2 % dpkg -l | grep apache
ii  apache-common                              1.3.34-4.1                             support files for all Apache webservers
ii  apache-ssl                                 1.3.34-4.1                             versatile, high-performance HTTP server with
ii  apache2                                    2.2.3-3.2ubuntu0.1                     Next generation, scalable, extendable web se
ii  apache2-mpm-prefork                        2.2.3-3.2ubuntu0.1                     Traditional model for Apache HTTPD 2.1
ii  apache2-utils                              2.2.3-3.2ubuntu0.1                     utility programs for webservers
ii  apache2.2-common                           2.2.3-3.2ubuntu0.1                     Next generation, scalable, extendable web se
rc  libapache2-mod-auth-mysql                  4.3.9-2.1ubuntu2                       Apache 2 module for MySQL authentication
ii  libapache2-mod-php5                        5.2.1-0ubuntu1.4                       server-side, HTML-embedded scripting languag


```

i need help!

---

### Post by vizitorq on 2007-10-22
yeah, i just re-apt-get installed it. it runs now. thanks for the help. this was very very important.

---

