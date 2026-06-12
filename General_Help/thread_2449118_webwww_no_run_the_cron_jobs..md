---
title: "web/www no run the cron jobs."
date: 2020-08-20
forum: General Help
---

### Post by fredy50 on 2020-08-20
Hello,

I try to create a cron jobs every hour

My example is:
52 * * * * www-data [http://url.com/to/web](http://url.com/to/web)

this will run every hour at 52.
i have try: (sudo nano /etc/default/cron) and (sudo nano /etc/crontab)

after that (sudo service cron restart)

can someone tell me why i can't create cron every time at 52 (a website)

Best Regards
Frederik Lundgaard Frandsen

---

### Post by sdsurfer on 2020-08-20
Is the cron daemon running?[FONT=Courier New][/FONT]

```

ps -ef | grep crond

```

If so, error in the cron tab?

---

### Post by fredy50 on 2020-08-20
Here is my output
```

hostings 28772 27203  0 16:45 pts/1    00:00:00 grep --color=auto crond
```

---

### Post by fredy50 on 2020-08-20
sudo service cron status

```
&#9679; cron.service - Regular background program processing daemon
   Loaded: loaded (/lib/systemd/system/cron.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2020-08-20 15:59:29 CEST; 47min ago
     Docs: man:cron(8)
 Main PID: 28271 (cron)
    Tasks: 1
   Memory: 284.0K
      CPU: 28ms
   CGroup: /system.slice/cron.service
           &#9492;&#9472;28271 /usr/sbin/cron -f

Aug 20 16:00:01 hostings cron[28271]: (root) INSECURE MODE (mode 0600 expected) (crontabs/root)
Aug 20 16:09:01 hostings CRON[28337]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 20 16:09:01 hostings CRON[28338]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/sy
Aug 20 16:09:01 hostings CRON[28337]: pam_unix(cron:session): session closed for user root
Aug 20 16:17:01 hostings CRON[28511]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 20 16:17:01 hostings CRON[28512]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 20 16:17:01 hostings CRON[28511]: pam_unix(cron:session): session closed for user root
Aug 20 16:39:01 hostings CRON[28596]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 20 16:39:01 hostings CRON[28597]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/sy
Aug 20 16:39:01 hostings CRON[28596]: pam_unix(cron:session): session closed for user root
```

---

### Post by SeijiSensei on 2020-08-20
```
52 * * * * www-data http://url.com/to/web
```

You don't have an executable program there, just a URL. What are you trying to accomplish? 

Maybe 

```
52 * * * * www-data curl -o  /home/me/output.html http://url.com/to/web
```

or

```
52 * * * * www-data wget -O /home/me/output.html http://url.com/to/web 
```

---

### Post by fredy50 on 2020-08-20
Here is what i try:
52 * * * * www-data wget -O [http://url.com/to/web](http://url.com/to/web)

Is it the right file? edit (sudo nano /etc/default/cron) ???

sudo service cron status:
```
&#9679; cron.service - Regular background program processing daemon
   Loaded: loaded (/lib/systemd/system/cron.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2020-08-20 17:56:47 CEST; 10s ago
     Docs: man:cron(8)
 Main PID: 29371 (cron)
    Tasks: 1
   Memory: 284.0K
      CPU: 3ms
   CGroup: /system.slice/cron.service
           &#9492;&#9472;29371 /usr/sbin/cron -f

Aug 20 17:56:47 hostings systemd[1]: cron.service: Ignoring invalid environment assignment '58 * * * * www-data wget -O http://url.com/to/web': /etc/default/cron
Aug 20 17:56:47 hostings systemd[1]: Started Regular background program processing daemon.
Aug 20 17:56:47 hostings cron[29371]: (CRON) INFO (pidfile fd = 3)
Aug 20 17:56:47 hostings cron[29371]: (root) INSECURE MODE (mode 0600 expected) (crontabs/root)
Aug 20 17:56:47 hostings cron[29371]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
```

---

### Post by SeijiSensei on 2020-08-20
No, that's not right either.  The -O option to wget directs the result to the file specified after the option, "/home/me/output.html" in the example above. And you want to add the entry to /etc/crontab.  Did you read any documentation before trying this?  Take a look at [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto).

I suggest you start by running 
```
wget http://url.com/to/web
```
from the command prompt and see what results. Then you can decide what to do next.  

wget has a ton of options. To see them run "wget --help".

You still didn't tell us what you're trying to do (beyond running something on an hourly basis).

---

