---
title: "Systemd Services Don't Work"
date: 2015-10-06
forum: General Help
---

### Post by Brando569 on 2015-10-06
I have a few usenet programs that I downloaded from GitHub and they didn't come with Systemd unit files so I grabbed a few from the net, even after modifying them with the correct arguments none of them work. The strange thing is that if I copy the **ExecStart** line and paste it into the terminal it runs as expected. They all complain about the same error since they all python scripts.

Here's one for SickRage
```
[Unit]
Description=SickRage Daemon

[Service]
User=root
Group=wheel

Type=forking
GuessMainPID=no
ExecStart=/usr/bin/python /opt/usenet/sickrage/SickBeard.py -q --daemon --nolaunch --datadir=/opt/usenet/sickrage

[Install]
WantedBy=multi-user.target

```

Here's the error from journalctl -xe
```
Oct 06 09:54:50 odroid systemd[1]: Starting SickRage Daemon...
-- Subject: Unit sickrage.service has begun start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit sickrage.service has begun starting up.
Oct 06 09:54:50 odroid systemd[9457]: Failed at step GROUP spawning /usr/bin/python: No such process
-- Subject: Process /usr/bin/python could not be executed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- The process /usr/bin/python could not be executed and failed.
-- 
-- The error number returned by this process is 3.
Oct 06 09:54:50 odroid systemd[1]: sickrage.service: control process exited, code=exited status=216
Oct 06 09:54:50 odroid systemd[1]: Failed to start SickRage Daemon.
-- Subject: Unit sickrage.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit sickrage.service has failed.
-- 
-- The result is failed.
Oct 06 09:54:50 odroid systemd[1]: Unit sickrage.service entered failed state.
Oct 06 09:54:50 odroid systemd[1]: sickrage.service failed.
Oct 06 09:54:50 odroid polkitd(authority=local)[589]: Unregistered Authentication Agent for unix-process:9452:3944808 (system bus name :1.47, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
```

```
 [root@odroid /opt]# status sickrage
&#9679; sickrage.service - SickRage Daemon
   Loaded: loaded (/etc/systemd/system/sickrage.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2015-10-06 09:54:50 EDT; 2min 8s ago
  Process: 9457 ExecStart=/usr/bin/python /opt/usenet/sickrage/SickBeard.py -q --daemon --nolaunch --datadir=/opt/usenet/sickrage (code=exited, status=216/GROUP)

Oct 06 09:54:50 odroid systemd[1]: Starting SickRage Daemon...
Oct 06 09:54:50 odroid systemd[1]: sickrage.service: control process exited, code=exited status=216
Oct 06 09:54:50 odroid systemd[1]: Failed to start SickRage Daemon.
Oct 06 09:54:50 odroid systemd[1]: Unit sickrage.service entered failed state.
Oct 06 09:54:50 odroid systemd[1]: sickrage.service failed.
```

Python definitely exists and is executable so I have no idea why it's complaining
```

 [root@odroid /opt]# ls -lh /usr/bin|grep python
lrwxrwxrwx 1 root root       9 Mar 17  2015 python -> python2.7
lrwxrwxrwx 1 root root       9 Mar 17  2015 python2 -> python2.7
-rwxr-xr-x 1 root root    2.5M Apr  2  2015 python2.7
```

```
 [root@odroid /opt]# python
Python 2.7.9 (default, Apr  2 2015, 16:04:32) 
[GCC 4.9.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

---

### Post by Brando569 on 2015-10-06
Actually it's happening with binary files also.

```
-- Unit nzbget.service has finished starting up.
-- 
-- The start-up result is done.
Oct 06 19:32:55 odroid systemd[1]: Starting NZBGet Daemon...
-- Subject: Unit nzbget.service has begun start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit nzbget.service has begun starting up.
Oct 06 19:32:55 odroid systemd[603]: Failed at step GROUP spawning /usr/bin/nzbget: No such process
-- Subject: Process /usr/bin/nzbget could not be executed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- The process /usr/bin/nzbget could not be executed and failed.
-- 
-- The error number returned by this process is 3.
Oct 06 19:32:55 odroid systemd[1]: nzbget.service: main process exited, code=exited, status=216/GROUP
Oct 06 19:32:55 odroid systemd[606]: Failed at step GROUP spawning /usr/bin/nzbget: No such process
-- Subject: Process /usr/bin/nzbget could not be executed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- The process /usr/bin/nzbget could not be executed and failed.
-- 
-- The error number returned by this process is 3.
Oct 06 19:32:55 odroid systemd[1]: nzbget.service: control process exited, code=exited status=216
Oct 06 19:32:55 odroid systemd[1]: Unit nzbget.service entered failed state.
```

---

### Post by sandyd on 2015-10-06
Problem possibly in
```


```

There is no wheel group for Debian based distros, though Redhat based distros have a wheel group.

Change it to
```
Group=root

```

Side note: Not a good idea to run processes as root, if they are compromised, they have free reign of the system.

---

### Post by Brando569 on 2015-10-08
Changing the group from wheel to root got rid of that error but the services still fail to start.

```
 [root@odroid /opt]# start couchpotato
Job for couchpotato.service failed. See "systemctl status couchpotato.service" and "journalctl -xe" for details.
 [root@odroid /opt]# status couchpotato
&#9679; couchpotato.service - An automatic NZB and torrent movie downloader
   Loaded: loaded (/etc/systemd/system/couchpotato.service; enabled; vendor preset: enabled)
   Active: failed (Result: timeout) since Thu 2015-10-08 21:02:33 EDT; 6min ago
  Process: 20256 ExecStart=/usr/bin/python /opt/usenet/couchpotato/CouchPotato.py --daemon --console_log --pid_file=/run/couchpotato/couchpotato.pid (code=exited, status=0/SUCCESS)
 Main PID: 5001 (code=exited, status=0/SUCCESS)

Oct 08 21:01:03 odroid systemd[1]: Starting An automatic NZB and torrent movie downloader...
Oct 08 21:01:04 odroid systemd[1]: PID file /run/couchpotato/couchpotato.pid not readable (yet?) after start.
Oct 08 21:02:33 odroid systemd[1]: couchpotato.service start operation timed out. Terminating.
Oct 08 21:02:33 odroid systemd[1]: Failed to start An automatic NZB and torrent movie downloader.
Oct 08 21:02:33 odroid systemd[1]: Unit couchpotato.service entered failed state.
Oct 08 21:02:33 odroid systemd[1]: couchpotato.service failed.
```

---

