---
title: "db2 autostart"
date: 2017-06-05
forum: General Help
---

### Post by przytula on 2017-06-05
having ubuntu
Linux db2 4.4.0-78-generic #99-Ubuntu SMP Thu Apr 27 15:29:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
in a vm and installed DB2
wanted to configure autostart and followed some instructions
created a file db2fmcd.conf in /etc/init with
# Starts fmcd
description "Fault Monitor is the DB2 database facility that monitors DB2 database manager instances, and restarting any instance that exits prematurely."
version "11.1.0.1"
start on stopped rc RUNLEVEL=[2345]
stop on starting rc RUNLEVEL=[016]
console output
respawn
respawn limit 10 120
exec /opt/IBM/db2/V11.1/bin/db2fmcd

after a boot : the process is not started or failed ?
where can I find msgs about this startup : dmesg did not contain any about this..
any logs about each process start or general log ?

thanks for all update/help
best regards, Guy Przytula

---

### Post by ian-weisser on 2017-06-05
Looks like you are using Ubuntu 16.04, which doesn't use sysvinit nor runlevels anymore.

A link to those instructions would be helpful.

Generally, I use systemd targets to launch services before user-login, or the user's .config/autostart dir to launch applications after user-login.
But there are many ways to do it.

---

### Post by przytula on 2017-06-06
ok
tried to create /etc/systemd/system/db2fmcd.service     with
infocura@db2:~$ cat /etc/systemd/system/db2fmcd.service
[Unit]
Description=db2 fault monitor coord daemon


[Service]
ExecStart=/opt/IBM/db2/V11.1/bin/db2fmcd
Restart=on-failure
Type=notify

if I enable and start manually : all ok - process started
if I reboot : the process is not up
no entry in dmesg..
where can we see the log of these startup services ?
best regards, Guy Przytula

---

### Post by ian-weisser on 2017-06-06
How did you tell systemd which target to use?

---

### Post by przytula on 2017-06-07
i checked also
infocura@db2:~$ ps -p1 | grep systemd && echo systemd || echo upstart
    1 ?        00:00:01 systemd
systemd



in the service file : [COLOR=#000000]ExecStart=/opt/IBM/db2/V11.1/bin/db2fmcd
systemctl daemon-reload
systemctl enable db2fmcd.service
systemctl start db2fmcd.service    (manual start=ok)
best regards, Guy przytula[/COLOR]

---

### Post by ian-weisser on 2017-06-07
It's not enough to merely create the service.
You must tell systemd exactly when you want the service started.

Maybe your service needs network access. Maybe it needs a printer or bluetooth.
systemd uses a series of 'targets' (directories called 'some_event.target') to determine what to start and when.
You place (or link) your .service file into the appropriate target.

See your available targets using
```
ls /etc/systemd/system/ | grep target
```

EXAMPLE: Let's see what service get started after a printer becomes available. You can see that it's CUPS.
```
$ ls -l /etc/systemd/system/printer.target.wants/
total 0
lrwxrwxrwx 1 root root 32 Dec 18  2014 cups.service -> /lib/systemd/system/cups.service



```


An even bigger list of (mostly unused) targets is at
```
ls /lib/systemd/system/ | grep target
```

The manpage for systemd targets is 'man systemd.targets'

---

### Post by przytula on 2017-06-07
thanks for the update
the service is independent - does not need any other service
just a daemon to start db2
I will check your comment
best regards, Guy

---

