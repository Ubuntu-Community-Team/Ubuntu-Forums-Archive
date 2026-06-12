---
title: "Latest update broke transmission - help"
date: 2018-03-05
forum: General Help
---

### Post by yuri-weinstein on 2018-03-05
On two system latest update broke transmission daemon:

```
Setting up transmission-daemon (2.93-1ubuntu1~16.04.1ubuntu1) ...
Job for transmission-daemon.service failed because the control process exited with error code. See "systemctl status transmission-daemon.service" and "journalctl -xe" for details.
invoke-rc.d: initscript transmission-daemon, action "start" failed.
\u25cf transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-03-04 15:11:13 PST; 10ms ago
  Process: 12578 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=217/USER)
 Main PID: 12578 (code=exited, status=217/USER)


Mar 04 15:11:13 xenial-vm systemd[1]: Starting Transmission BitTorrent Daemon...
Mar 04 15:11:13 xenial-vm systemd[1]: transmission-daemon.service: Main process exited, code=exited, status=217/USER
Mar 04 15:11:13 xenial-vm systemd[1]: Failed to start Transmission BitTorrent Daemon.
Mar 04 15:11:13 xenial-vm systemd[1]: transmission-daemon.service: Unit entered failed state.
Mar 04 15:11:13 xenial-vm systemd[1]: transmission-daemon.service: Failed with result 'exit-code'.
dpkg: error processing package transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up transmission (2.93-1ubuntu1~16.04.1ubuntu1) ...
Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



Any help appreciated!

---

### Post by PleasantPersonablePenguins on 2018-03-05
same here. tried complete uninstall/reinstall and played with users/rights - no luck.

```
Setting up transmission-daemon (2.93-1ubuntu1~16.04.1ubuntu1) ...
Job for transmission-daemon.service failed because a timeout was exceeded. See "systemctl status transmission-daemon.service" and "journalctl -xe" for details.
invoke-rc.d: initscript transmission-daemon, action "start" failed.
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: timeout) since Mon 2018-03-05 20:02:56 MSK; 12ms ago
  Process: 2994 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=0/SUCCESS)
 Main PID: 2994 (code=exited, status=0/SUCCESS)

Mar 05 20:01:25 torr systemd[1]: Starting Transmission BitTorrent Daemon...
Mar 05 20:02:55 torr systemd[1]: transmission-daemon.service: Start operation timed out. Terminating.
Mar 05 20:02:56 torr systemd[1]: Failed to start Transmission BitTorrent Daemon.
Mar 05 20:02:56 torr systemd[1]: transmission-daemon.service: Unit entered failed state.
Mar 05 20:02:56 torr systemd[1]: transmission-daemon.service: Failed with result 'timeout'.
dpkg: error processing package transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
```

it takes around one minute before this error (timeout), while rpc is working during this period and you can connect to daemon from outside and see existing torrents. and then it just stops.

---

### Post by yuri-weinstein on 2018-03-05
No good, also see [https://github.com/transmission/transmission/issues/538](https://github.com/transmission/transmission/issues/538)

---

### Post by PleasantPersonablePenguins on 2018-03-06
Here is temporary solution from other thread [https://ubuntuforums.org/showthread.php?t=2386355](https://ubuntuforums.org/showthread.php?t=2386355) (direct link [https://ubuntuforums.org/showthread.php?t=2386355&page=2&p=13745879#post13745879](https://ubuntuforums.org/showthread.php?t=2386355&page=2&p=13745879#post13745879))


[LIST=1]
[*]build your own from source and do not forget to install libsystemd-dev before building.
[*]wait for the PPA maintainer to do the above and build a new version.
[*]change the type in **/etc/systemd/system/transmission-daemon.service** from "notify" to "simple"
[/LIST]

By Talz1979

Third one seems the simpliest and works for me.

---

### Post by yuri-weinstein on 2018-03-06
Thank you !

---

### Post by yuri-weinstein on 2018-03-07
@PleasantPersonablePenguins 

I tried =>
[LIST=1]
[*]change the type in **/etc/systemd/system/transmission-daemon.service** from "notify" to "simple"
[/LIST]
And it did not work :(

Any clues?

---

### Post by yuri-weinstein on 2018-03-10
Anybody has found solution to this  ?

---

### Post by #&amp;thj^% on 2018-03-10
> **yuri-weinstein said:**
> Anybody has found solution to this  ?

Did you ever try for "transmission-daemon 2.93"
To creatting this file:
```
/etc/systemd/system/transmission-daemon.service.d/override.conf
```
with this content:
```
[Service]
User=
Type=
Type=simple
User=debian-transmission
Group=debian-transmission
```
reload systemd config:
```
systemctl daemon-reload
```
and execute:
```
systemctl start transmission-daemon.service
```

---

### Post by yuri-weinstein on 2018-03-10
@1fallen

It kinda helped ! I can start transmission and see green status, but can not login.  Not as my original user not as  debian-transmission user.  Although maybe I need to setup transmission user again ?!

Thanks for looking !

---

### Post by #&amp;thj^% on 2018-03-10
> **yuri-weinstein said:**
> @1fallen

It kinda helped ! I can start transmission and see green status, but can not login.  Not as my original user not as  debian-transmission user.  Although maybe I need to setup transmission user again ?!

Thanks for looking !
Well let's have a peek at:
```
nano /etc/systemd/system/transmission-daemon.service.d/override.conf
```
paste back here please

---

### Post by yuri-weinstein on 2018-03-11
[COLOR=#000000]*@1fallen*[/COLOR]

I actually don't have file /etc/systemd/system/transmission-daemon.service.d/override.conf

I have  /lib/systemd/system/transmission-daemon.service.d/override.conf (which I guess I'd added, maybe wrongly (??), sorry for being clueless) with:

> [Service]
User=
Type=
Type=simple
User=debian-transmission
Group=debian-transmission

I also have /lib/systemd/system/transmission-daemon.service (from original install)

> [Unit]
Description=Transmission BitTorrent Daemon
After=network.target

[Service]
User=transmission
Type=simple
ExecStart=/usr/bin/transmission-daemon -f --log-error
ExecReload=/bin/kill -s HUP $MAINPID

[Install]
WantedBy=multi-user.target 

---

### Post by #&amp;thj^% on 2018-03-11
> **yuri-weinstein said:**
> [COLOR=#000000]*@1fallen*[/COLOR]

I actually don't have file /etc/systemd/system/transmission-daemon.service.d/override.conf

I have  /lib/systemd/system/transmission-daemon.service.d/override.conf (which I guess I'd added, maybe wrongly (??), sorry for being clueless) with:



I also have /lib/systemd/system/transmission-daemon.service (from original install)
Well you should add that then (/etc/systemd/system/transmission-daemon.service.d/override.conf)
With PPA's version 2.93 and systemd just did not mix well.
BTW I don't use the "transmission-daemon" or the PPA but that's just my choice! (To be noted only)

---

### Post by yuri-weinstein on 2018-03-12
Ok finally I got it working !
also ref: [https://github.com/transmission/transmission/issues/537](https://github.com/transmission/transmission/issues/537)

Thank you  *@1fallen *!

---

### Post by BalleClorin on 2018-03-21
Added this workaround to the PPA now, building as I type this. My apologies for the delay, life kind of gets in te way all the time.
If anyone has any ideas on how to fix the notify problem please let me know. I don't have much time to investigate.

---

