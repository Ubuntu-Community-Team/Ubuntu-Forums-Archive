---
title: "apache help please"
date: 2006-12-02
forum: General Help
---

### Post by highneko on 2006-12-02
Hello, I have installed Apache on my old computer that's connected to the internet using a router. Apache is always running, but I can't control it.
When I type "apache2ctl start" it says:
```
highneko@ubuntu:~$ apache2ctl start
(13): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
highneko@ubuntu:~$
```
When I type "apache2ctl stop" it says:
```
highneko@ubuntu:~$ apache2ctl stop
httpd (pid 4469?) not running
highneko@ubuntu:~$
```
And when I type "ps -e | grep apache" it says:
```
highneko@ubuntu:~$ ps -e | grep apache
 4469 ?        00:00:00 apache2
 4470 ?        00:00:00 apache2
 4471 ?        00:00:00 apache2
 4473 ?        00:00:00 apache2
highneko@ubuntu:~$
```
I can connect to my website by entering my computers dynamic address, but can't get it to connect when I type my static address, maybe someone can help me get this working? 

Maybe someone can explain how to get Apache to stop starting automatically when I boot? I would like to start it manually.

---

