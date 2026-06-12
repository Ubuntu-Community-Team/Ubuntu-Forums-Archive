---
title: "cups error with HP F4140"
date: 2008-04-09
forum: General Help
---

### Post by thefunnyman on 2008-04-09
I bought an HP F4140 all-in-one a couple of weeks ago to replace my useless lexmark printer.  I got home with the printer and was delighted to realize that I had to do absolutely nothing to configure the printer for 7.10.  However, last week, the printer just stopped working.  /var/log/cups/error_log output is below.

```

E [09/Apr/2008:14:28:48 -0500] PID 32381 (/usr/lib/cups/backend/hp) stopped with status 127!
E [09/Apr/2008:14:28:51 -0500] PID 32380 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [09/Apr/2008:14:34:00 -0500] PID 32446 (/usr/lib/cups/backend/hp) stopped with status 127!
E [09/Apr/2008:14:34:02 -0500] PID 32445 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [09/Apr/2008:14:39:12 -0500] PID 32514 (/usr/lib/cups/backend/hp) stopped with status 127!
E [09/Apr/2008:14:39:13 -0500] PID 32513 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [09/Apr/2008:14:44:23 -0500] PID 32572 (/usr/lib/cups/backend/hp) stopped with status 127!
E [09/Apr/2008:14:44:24 -0500] PID 32571 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [09/Apr/2008:14:49:34 -0500] PID 32633 (/usr/lib/cups/backend/hp) stopped with status 127!
E [09/Apr/2008:14:49:36 -0500] PID 32632 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [09/Apr/2008:14:49:36 -0500] [Job 153] Canceling job since it could not be sent after 5 tries.

```

I've searched google and the forums and haven't been able to find much relevant information regarding the errors i'm getting.  I sincerely apologize if this has been discussed elsewhere and I just haven't found it.  Can anyone help me to understand why my printer just all of a sudden stopped working?  Tried restarting cups and restarting the machine to no avail.  I do not RECALL updating cups recently, but I could be horribly mistaken as I have the memory of a gnat.

Thanks so much in advance for any help anyone can provide.

thefunnyman

---

### Post by warp99 on 2008-04-09
I would first set the log level in the file /etc/cups/cupsd.conf from 'warning" to 'debug', then restart the cups service:

```
sudo /etc/init.d/cups restart
```

Then you can get a more detailed output of the problem. Per the cups website:

[http://www.cups.org/articles.php?L198+I0+TFAQ+P1+Q](http://www.cups.org/articles.php?L198+I0+TFAQ+P1+Q)

---

### Post by thefunnyman on 2008-05-08
Thanks for all your help...Sorry for taking so long to reply...I couldn't make too much sense of what was wrong by digging through the logs, but I did find references that led me to believe that there was some driver hiccup.  So I reinstalled the drivers from hp's website and it works just fine now.

Thanks again.

---

