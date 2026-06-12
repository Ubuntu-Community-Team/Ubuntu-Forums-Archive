---
title: "why the apache2 does not start correctly?"
date: 2007-05-18
forum: General Help
---

### Post by longbow on 2007-05-18
When I try to start the apache2 via "apache2ctl start", it gives
[COLOR="Blue"]apache cannot find a reliable fully qualified domain name, using 127.0.0.1 as host name ....[/COLOR]

It seems the apache is not running at all. When I type 127.0.0.1 or localhost in firefox, it says the server can not be found. Via "[COLOR="Blue"]ps -ef[/COLOR]", there is no apache or httpd running.

In the [COLOR="Blue"]administration->service[/COLOR] configuration,  apache is checked, so maybe it implies it should be started automatically at boot time.

Mine is ubuntu 7.0.4, with apache 2.2. Thanks in advance.

---

### Post by total wormage on 2007-05-18
you'll need to edit the config file manually in apache2 before it does _anything_

your answer is [here]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-42714b7a81f075c4f6024b8e0a36e2fccb11fdbd")

---

### Post by longbow on 2007-05-18
Thanks, but another problem arises.
After I do as you told, the previous error did resolved. But the apache still can not be started. This time nothing is outputted when I issue "sudo /usr/sbin/apache2ctl start".
When I issue "sudo /usr/sbin/apache2ctl stop", it tolds me 
httpd (no pid file) not running.


> **total wormage said:**
> you'll need to edit the config file manually in apache2 before it does _anything_

your answer is [here]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-42714b7a81f075c4f6024b8e0a36e2fccb11fdbd")

---

### Post by total wormage on 2007-05-18
> **longbow said:**
> Thanks, but another problem arises.
After I do as you told, the previous error did resolved. But the apache still can not be started. This time nothing is outputted when I issue "sudo /usr/sbin/apache2ctl start".
When I issue "sudo /usr/sbin/apache2ctl stop", it tolds me 
httpd (no pid file) not running.

ok, make sure that this line is in your apache2.conf

```
PidFile /var/run/apache2.pid
```

it is odd that this problem occurred, i just installed apache2.2 and i only had to set the servername, but even without the server would start and i could browse to it.

i suggest if there occur more problems you read up a bit at [http://httpd.apache.org/docs/2.2/]("http://httpd.apache.org/docs/2.2/")

:], good luck!

---

### Post by longbow on 2007-05-18
That line already exits. However, after I restarted my computer, the apache finally works. 
Thanks a lot!

[QUOTE=total wormage;2677456]ok, make sure that this line is in your apache2.conf

```
PidFile /var/run/apache2.pid
```

---

