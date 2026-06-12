---
title: "Systemd with Shell script with loop"
date: 2015-12-10
forum: General Help
---

### Post by albert42 on 2015-12-10
Hi,

I have tried the following but it does not work as systemd is waiting for the loop to complete. In this instance the loop is a infinite one.  I need help to get this working. Thanks,

```
#!/bin/sh
# Shell Script named live.sh
while true
do
 /usr/bin/livestats
 sleep 5
done

```


```
# Live Stats
# =======================
#
#
[Unit]
Description=Live Statistics
After=network.target


[Service]
Type=oneshot
ExecStart=/usr/bin/live.sh
KillMode=mixed


[Install]
WantedBy=multi-user.target



```

---

### Post by matt_symes on 2015-12-10
Hi

> **albert42 said:**
> Hi,

I have tried the following but it does not work as systemd is waiting for the loop to complete. In this instance the loop is a infinite one.  I need help to get this working. Thanks,

```
#!/bin/sh
# Shell Script named live.sh
while true
do
 /usr/bin/livestats
 sleep 5
done

```


```
# Live Stats
# =======================
#
#
[Unit]
Description=Live Statistics
After=network.target


[Service]
Type=oneshot
ExecStart=/usr/bin/live.sh
KillMode=mixed


[Install]
WantedBy=multi-user.target



```

I've not much experience with systemd as I've been using 14.04 until the last week or so.

However, have you explored the system service options Restart and RestartSec.

> 
Restart=
	   Configures whether the service shall be restarted when the service
	   process exits, is killed, or a timeout is reached. The service
	   process may be the main service process, but also one of the
	   processes specified with ExecStartPre=, ExecStartPost=, ExecStop=,
	   ExecStopPost=, or ExecReload=. When the death of the process is a
	   result of systemd operation (e.g. service stop or restart), the
	   service will not be restarted. Timeouts include missing the
	   watchdog "keep-alive ping" deadline and a service start, reload,
	   and stop operation timeouts.

RestartSec=
	   Configures the time to sleep before restarting a service (as
	   configured with Restart=). Takes a unit-less value in seconds, or a
	   time span value such as "5min 20s". Defaults to 100ms.

That way you'll be able to remove the sleep command from your script.

BTW: What is livestats ?

Kind regards

---

### Post by albert42 on 2015-12-10
Hi,

That sounds like a good idea.  livestats is a program i clobbered together to get system utilization stats related  CPU, Network and Disk written in Lua.  I am hopeless with regards to C or C++ programming.   Thanks.

---

### Post by matt_symes on 2015-12-10
Hi

Please post back with the solution you come up with. I, for one, would be interested in seeing if it works for you.

If it does work then please mark the thread as [SOLVED] using the thread tools at the top of this page. It'll help others looking for a solution.

Kind regards

---

### Post by albert42 on 2015-12-11
Hi,

I have tried but it did not work.  Systemd does not restart a script RestartSec, i guess it will only restart if the ExecStart fail to start.

---

### Post by QDR06VV9 on 2015-12-11
[COLOR=#222426][FONT=Helvetica Neue]systemd service management only knows about service units. These automatically (re-)generated service units are written to invoke the system 5 rc scripts. They have, amongst other things:
This is just an Example not meant to solve your script, But maybe point to a solution..
[/FONT][/COLOR]> [Unit]
SourcePath=/etc/init.d/wibble
[Service]
ExecStart=/etc/init.d/wibble start

ExecStop=/etc/init.d/wibble stop[COLOR=#222426][FONT=Helvetica Neue]
Good Read here [http://unix.stackexchange.com/questions/233468/how-does-systemd-use-etc-init-d-scripts](http://unix.stackexchange.com/questions/233468/how-does-systemd-use-etc-init-d-scripts)
[http://www.freedesktop.org/software/systemd/man/systemd.service.html](http://www.freedesktop.org/software/systemd/man/systemd.service.html)

Systemd at least for me has been my biggest Puzzle when creating scripts.
Hope there is something useful there..
Kind Regards[/FONT][/COLOR]

---

### Post by matt_symes on 2015-12-11
Hi

> **albert42 said:**
> Hi,

I have tried but it did not work.  Systemd does not restart a script RestartSec, i guess it will only restart if the ExecStart fail to start.
```

matthew-xu-16-04:/home/matthew:1 % cat test.sh 
#!/bin/sh

echo $(date) >> /home/matthew/test.log
matthew-xu-16-04:/home/matthew:1 % ls -al test.sh 
-rwxr-xr-x 1 matthew matthew 50 Dec 11 21:11 test.sh*
matthew-xu-16-04:/home/matthew:1 % cat /etc/systemd/system/multi-user.target.wants/test.service
# Live Stats
# =======================
#
#
[Unit]
Description=test
After=network.target


[Service]
Type=simple
ExecStart=/home/matthew/test.sh
KillMode=mixed
RestartSec=5
Restart=always


[Install]
WantedBy=multi-user.target
matthew-xu-16-04:/home/matthew:1 % sudo systemctl daemon-reload                                
matthew-xu-16-04:/home/matthew:1 % sudo service test start 
matthew-xu-16-04:/home/matthew:1 % sudo service test stop
matthew-xu-16-04:/home/matthew:1 % 
```

Output.
```

matthew-xu-16-04:/home/matthew:2 % tail -f ~/test.log
Fri Dec 11 21:11:55 GMT 2015
Fri Dec 11 21:12:00 GMT 2015
Fri Dec 11 21:12:06 GMT 2015
Fri Dec 11 21:12:11 GMT 2015
Fri Dec 11 21:12:16 GMT 2015
```

Post your script and your new service files.

Kind regards

---

