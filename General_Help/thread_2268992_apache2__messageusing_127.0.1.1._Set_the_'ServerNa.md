---
title: "apache2  message:using 127.0.1.1. Set the 'ServerName' directive globally"
date: 2015-03-12
forum: General Help
---

### Post by shamsat on 2015-03-12
apache2 is working in ubuntu 14.10, but when i run the command "service apache2 reload" get this message:
> 
 * Restarting web server apache2                                                  AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message

In the /etc/hosts the 127.0.1.1 is for myhost name not fully qualified domain name like myhost.example.com:
> 
127.0.1.1 myhost


---

### Post by dragonfly41 on 2015-03-13
Follow the tips here ...

[http://askubuntu.com/questions/256013/could-not-reliably-determine-the-servers-fully-qualified-domain-name](http://askubuntu.com/questions/256013/could-not-reliably-determine-the-servers-fully-qualified-domain-name)

i.e. create new file in /etc/apache2/conf-available/fqdn.conf

containing ... ServerName localhost

---

### Post by shamsat on 2015-03-14
Thanks for  reply the problem solved.

---

