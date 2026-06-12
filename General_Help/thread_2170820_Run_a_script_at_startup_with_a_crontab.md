---
title: "Run a script at startup with a crontab ?"
date: 2013-08-27
forum: General Help
---

### Post by cogset on 2013-08-27
I've tried to run a script at start up for stopping apache2 and cups services,using a cronjob:the idea is to stop but not disable those services  since I occasionally use them,the  simple script in question is 
```
#!/bin/sh

sudo service apache2 stop  && sudo service cups stop
```
it does actually work if I run it manually with sudo,it does't when I put it in a crontab like that 
```
  @reboot  /path/to/script
```
the script in question has 744 permissions and it is _not_ owned by root:since I've tried to run it with a root cronjob,maybe that is the issue?

---

### Post by ian-weisser on 2013-08-27
Well, since those services are started by root (or a system user), that cron job can't go in just *any* crontab...like your user crontab. It needs to be a root cron job and go in a root crontab like /etc/crontab or /etc/cron.d

Also, you may have trouble remembering exactly how you disabled those services in a few months, which may make re-enabling them difficult.
In addition, starting then stopping those services takes system resources and time.
A more elegant solution may be to disable each service's startup in /etc/init or /etc/init.d

---

### Post by CharlesA on 2013-08-27
The cheap and easy way to stop those services from running on start up is to remove the execute permission from the startup script in/etc/init.d/

/etc/init.d/apache2 and /etc/init.d/cups (I think, I don't use cups).

Now they won't run and you can give them back execute ability when you need to use them again.

---

### Post by ian-weisser on 2013-08-27
cups has startup scripts in both /etc/init/cups.conf and /etc/init.d/cups

---

### Post by cogset on 2013-08-28
Thanks,I was indeed after some simple script to edit,like I've done already for   /etc/init/avahi-daemon.conf,where I've just added "never" ```
the start on (never
          and filesystem
          and started dbus)
stop on stopping dbus
``` and this did the trick.

Turns out that cups (and apache2) configuration scripts are more complicated than that,I couldn't locate such simple lines to edit-I think for now I'll have to maybe follow the advice to just remove the execute permission for cups and apache scripts in /etc/init.d .

But why couldn't I just execute automatically the script ```
#!/bin/sh

sudo service apache2 stop  && sudo service cups stop
``` that I've listed above? After all,it does work if I run it manually,and I've put it in what* I think *is my root crontab,the one you edit with
 **sudo crontab -l**,to be clear:isn't that enough? Are**  -rwxr--r--** permissions wrong for that script to work in a crontab?

---

### Post by steeldriver on 2013-08-28
I believe that the 'clean' way to suppress automatic starting of jobs that are now controlled via upstart is to create a file called <service>.override containing the single word 'manual' in the /etc/init directory, e.g. to disable cups

```
echo "manual" | sudo tee /etc/init/cups.override
```

or

```
sudo sh -c "echo 'manual' > /etc/init/cups.override"
```

I just tried it for cups and it seemed to work.

Some advantages: it's transparent (a quick look in /etc/init tells anyone what's disabled - don't need to actually open the script(s) and look for modifications) and it won't get reverted by subsequent package updates (which changing the script's execute permission may, I think)

As to why your cronjob didn't work, I'm not very good with those but it's usually paths (does root's cron environment have /usr/sbin and /sbin in its PATH?) - or perhaps it's a matter of timing (exactly when during the reboot do 'reboot' cronjobs get executed - is it before the services you're trying to stop have even been started?)

---

### Post by cogset on 2013-08-30
Once again,thank you all for sharing so many useful tips:by the looks of it,as it often happens,there are many ways to do this.

And,before posting,I did forget that I had already run into this other solution  [http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up](http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up),which would be to put the script in** /etc/init.d/rc.local**.

This would probably work around the timing issue,I suppose:assuming the reason why a cronjob fails is a timing issue,which I don't know for sure.Would this be worth a try too ?

---

### Post by ian-weisser on 2013-08-30
> **cogset said:**
> assuming the reason why a cronjob fails is a timing issue
Cron jobs that fail usually have a problem with the job script, not timing.

---

### Post by steeldriver on 2013-08-30
> **ian-weisser said:**
> Cron jobs that fail usually have a problem with the job script, not timing.

Sorry, when I mentioned 'timing' I meant as a reason why the cronjob might have failed to stop the service (not suggesting the cronjob itself failed to run). For example, if I do

```

# m h  dom mon dow   command

@reboot /root/apache2.stop

```
where
```

#!/bin/sh

service apache2 stop
logger "ran service apache2 stop from crontab @reboot"

``` 

then after reboot

```

$ service apache2 status
Apache2 is running (pid 1473).

```

Now if I look at the logs
```

$ grep -i apache /var/log/syslog
Aug 30 17:29:18 lap-t61p CRON[1230]: (root) CMD (/root/apache2.stop)
Aug 30 17:29:20 lap-t61p logger: ran service apache2 stop from crontab @reboot

```

I see that the cronjob itself is logged at 17:29:**18** and the 'service stop' was issued before 17:29:**20**, however
```

$ tail -2 /var/log/apache2/error.log 
[Fri Aug 30 17:28:12 2013] [notice] caught SIGTERM, shutting down
[Fri Aug 30 17:29:25 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations

```

shows apache2 coming back up at 17:29:**25**

---

### Post by cogset on 2013-09-03
Well,after struggling with a cronjob that I could not get to work,I've just pasted these  lines** service apache2 stop && service cups stop** in the rc.local script and it worked straight away.

---

