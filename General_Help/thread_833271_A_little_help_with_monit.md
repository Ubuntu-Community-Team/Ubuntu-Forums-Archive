---
title: "A little help with monit"
date: 2008-06-18
forum: General Help
---

### Post by arthurbuliva on 2008-06-18
Hi All.

I have apt-install'ed monit successfully and configs seem to be ok apart from one thing:

```
check process apache2 with pidfile /usr/local/apache2/logs/httpd.pid
   group www-data
   start program  "/etc/init.d/apache2 start"
   stop program  "/etc/init.d/apache2 stop"
   if failed host localhost port 80 protocol http
      and request "/" then alert
   if cpu is greater than 60% for 2 cycles then alert
   if cpu > 80% for 5 cycles then restart
   if children > 250 then restart
   if loadavg(5min) greater than 10 for 8 cycles then alert
   if 3 restarts within 5 cycles then timeout
```

Is the part I intend it to monitor apache. I have tried changing the name to apache2, apache and httpd but I keep getting an email that 

'apache' process is not running or
'apache2' process is not running
and/or
'httpd' failed to start.

So I should ask my question: what is the "name" of the apache http service?

Thanks

---

