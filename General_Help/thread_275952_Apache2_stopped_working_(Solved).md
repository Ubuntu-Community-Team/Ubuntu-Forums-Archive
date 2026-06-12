---
title: "Apache2 stopped working (Solved)"
date: 2006-10-12
forum: General Help
---

### Post by seshomaru samma on 2006-10-12
I've been using apache2 to host a small website with my son's pix on it.
It worked perfectly for almost a year but after I came back from a 10days holiday it doesn't work anymore . When I run it I get :
```
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```
what can I do?
what happened ? maybe it's one of the updates? I havent updated my Ubuntu in a while but before I went on a holiday I updated a month worth of updates...

---

### Post by PriceChild on 2006-10-12
It sounds like another program is currently using port 80.

Bit wierd how it goes on about being unable to open logs.

Maybe a dpkg-reconfigure?

UPDATE

Could i first make sure that you are running it as root?

---

### Post by apjone on 2006-10-12
did you start apache as root?

---

### Post by PriceChild on 2006-10-12
> **apjone said:**
> did you start apache as root?He he we both added that the same time

---

### Post by apjone on 2006-10-12
Yeah, i was on a IM chat so I went post before you but I ended up taking ages before I clicked send cause my mate was bugging me rofl.

---

### Post by apjone on 2006-10-12
> **PriceChild said:**
> It sounds like another program is currently using port 80.

Bit wierd how it goes on about being unable to open logs.

Maybe a dpkg-reconfigure?

UPDATE

Could i first make sure that you are running it as root?

Just tested my server and yes, it looks like you need to be running as root.

use the following command to start apache

```
 sudo /etc/init.d/apache2 start 
```

---

### Post by seshomaru samma on 2006-10-12
thanks but i tried running as root before i posted (sudo apache2) and got the same error.
with sudo /etc/init.d/apache2 start
I get :
```
 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (pid 5398) already running
```
and ps ax says:
```
 5398 ?        Ss     0:00 /usr/sbin/apache2 -k start -DSSL
```
i would speculate that another programme is using port 80 ,cause :
```
sesho@ubuntu:~$ sudo apache2
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
```

how do i find which programme uses which port?

---

### Post by seshomaru samma on 2006-10-12
> how do i find which programme uses which port?
from the IRC i got this command :
```
netstat --all --programs | grep www
```
which showed that apache was working!
the reason i was not able to view what apache served was due to my router that decided to change my static ip to a dynamic one. i still don't know why i got those error massages but at least i know apache is running....

---

### Post by PriceChild on 2006-10-12
You might want to try a "force-reload" to get new settings to take effect.

---

