---
title: "autorun command every x minutes"
date: 2007-08-05
forum: General Help
---

### Post by phillips321 on 2007-08-05
Hi guys,

first problems, to run the program visitors i have to do this:
```
phillips321@LinuxServer:~$ cd /opt/visitors_0.7/
phillips321@LinuxServer:/opt/visitors_0.7$ ./visitors -A /var/log/thttpd.log > /media/data/visitors.html
--
85 lines processed in 1 seconds
0 invalid lines, 0 blacklisted referers
phillips321@LinuxServer:/opt/visitors_0.7$

```

why do i have to browse to the directory to run the script? can i not link the executable to somewhere such as /bin?

My next problem is that i want to automatically run this command every 5minutes, anyone here have any idea on how to autostart a batch file at boot then run it every 5minutes?

cheers

---

### Post by apetresc on 2007-08-05
> **phillips321 said:**
> Hi guys,

first problems, to run the program visitors i have to do this:
```
phillips321@LinuxServer:~$ cd /opt/visitors_0.7/
phillips321@LinuxServer:/opt/visitors_0.7$ ./visitors -A /var/log/thttpd.log > /media/data/visitors.html
--
85 lines processed in 1 seconds
0 invalid lines, 0 blacklisted referers
phillips321@LinuxServer:/opt/visitors_0.7$

```

why do i have to browse to the directory to run the script? can i not link the executable to somewhere such as /bin?

My next problem is that i want to automatically run this command every 5minutes, anyone here have any idea on how to autostart a batch file at boot then run it every 5minutes?

cheers

You sure can. For the first thing (adding it to the path), type:```
sudo ln -s /opt/visitors_0.7/visitors /usr/bin/visitors
``` Now you can run your script simply by typing ```
visitors
``` at the prompt.

For your second thing (running it every few minutes), check out the documentation for "cron", at, for example, here: [http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)

Hope this helps :)

---

### Post by phillips321 on 2007-08-05
worked great thanks

i had to type "crontab -e", this opened up nano and allowed me to add the process

00,05,10,15,20,25,30,35,40,45,50,55 * * * * visitors -A /var/logs/thttpd.log > /media/data/visitors.html

many thanks

P.s. this runs the process every 5 minutes

---

