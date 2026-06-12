---
title: "Fail to start Apache2"
date: 2018-04-30
forum: General Help
---

### Post by ethicalnoob on 2018-04-30
i just install apache2 today but when i wrote
sudo systemctl start apache2.service
it resulted in:
Job for apache2.service failed because the control process exited with error code.
See "systemctl  status apache2.service" and "journalctl  -xe" for details.
[SIZE=4]

Additional Information:
[SIZE=3]Command: [/SIZE][/SIZE]sudo systemctl status apache2.service

&#9679; apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: failed (Result: exit-code) since Mon 2018-04-30 18:31:19 EDT; 9min ago
  Process: 23167 ExecStart=/usr/sbin/apachectl start (code=exited, status=1/FAILURE)


Apr 30 18:31:19 frank-XPS-13-9360 apachectl[23167]: (98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
Apr 30 18:31:19 frank-XPS-13-9360 apachectl[23167]: (98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
Apr 30 18:31:19 frank-XPS-13-9360 apachectl[23167]: no listening sockets available, shutting down
Apr 30 18:31:19 frank-XPS-13-9360 apachectl[23167]: AH00015: Unable to open logs
Apr 30 18:31:19 frank-XPS-13-9360 apachectl[23167]: Action 'start' failed.
Apr 30 18:31:19 frank-XPS-13-9360 apachectl[23167]: The Apache error log may have more information.
Apr 30 18:31:19 frank-XPS-13-9360 systemd[1]: apache2.service: Control process exited, code=exited status=1
Apr 30 18:31:19 frank-XPS-13-9360 systemd[1]: Failed to start The Apache HTTP Server.
Apr 30 18:31:19 frank-XPS-13-9360 systemd[1]: apache2.service: Unit entered failed state.
Apr 30 18:31:19 frank-XPS-13-9360 systemd[1]: apache2.service: Failed with result 'exit-code'.


Please help.....

---

### Post by pqwoerituytrueiwoq on 2018-04-30
check the error log here:
[FONT=courier new]/var/log/apache2/error.log[/FONT]

---

### Post by TheFu on 2018-04-30
Welcome to the forums.

housekeeping.
* please don't change fonts without a good reason.
* Instead of start, try restart.

Address already bound means that some other daemon is already listening.  Could be apache. Could be something else.  Have you tried to access it?  Did that fail?  Does **lsof** or **netstat** show which process has grabbed 80/tcp or 443/tcp?  Is apache configured to listen on a specific NIC or not?

---

### Post by SeijiSensei on 2018-05-01
Usually when you install apache it configures itself to start at boot.  Maybe it's already running, and you didn't know it?  If you use "systemctl restart" rather than "start" it will close down any running instances then start up again.

You can see whether apache is running with the command:

```
ps ax | grep apache
```

If it's running, you'll see a result like this:

```

  444 ?        Ss     0:00 /usr/sbin/apache2 -k start
  445 ?        Sl     0:00 /usr/sbin/apache2 -k start
  446 ?        Sl     0:00 /usr/sbin/apache2 -k start

```

---

### Post by ethicalnoob on 2018-05-01
it is not running i just check 
( edit ) nothing really happens until I search up some solution and this happened

6007 pts/0    T      0:00 sudo nano /etc/apache2/conf.d/fqdn
 6008 pts/0    T      0:00 nano /etc/apache2/conf.d/fqdn
 6019 pts/0    T      0:00 sudo nano /etc/apache2/conf.d/fqdn
 6020 pts/0    T      0:00 nano /etc/apache2/conf.d/fqdn
 6293 pts/0    T      0:00 sudo systemctl status apache2.service
 6294 pts/0    T      0:00 systemctl status apache2.service
 6471 pts/0    T      0:00 sudo nano /etc/apache2/conf-available/server-name.conf
 6472 pts/0    T      0:00 nano /etc/apache2/conf-available/server-name.conf
 6681 pts/0    T      0:00 systemctl status apache2.service
 6886 pts/0    S+     0:00 grep --color=auto apache

---

### Post by ethicalnoob on 2018-05-01
> **pqwoerituytrueiwoq said:**
> check the error log here:
[FONT=courier new]/var/log/apache2/error.log[/FONT]
i did sudo nano [FONT=&quot]/var/log/apache2/error.log and nothing happens
[/FONT]

---

### Post by ethicalnoob on 2018-05-01
> **TheFu said:**
> Welcome to the forums.

housekeeping.
* please don't change fonts without a good reason.
* Instead of start, try restart.

Address already bound means that some other daemon is already listening.  Could be apache. Could be something else.  Have you tried to access it?  Did that fail?  Does **lsof** or **netstat** show which process has grabbed 80/tcp or 443/tcp?  Is apache configured to listen on a specific NIC or not?

I try netstat but it only said tcp on the left. It didn't say anything about 80/tcp or 443/tcp and lsof just dump a bunch of stuffs i don't know.

---

### Post by ethicalnoob on 2018-05-01
i think i solve it; lighttpd was using socket :80

---

### Post by TheFu on 2018-05-01
> **ethicalnoob said:**
> i think i solve it; lighttpd was using socket :80

That would do it.
If the question is SOLVED, please mark it that way using the "Thread tools" button near the top. This helps the community.

---

