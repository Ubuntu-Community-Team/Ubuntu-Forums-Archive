---
title: "Errors were encountered while processing: exim4-daemon-heavy"
date: 2018-04-12
forum: General Help
---

### Post by shamsat on 2018-04-12
I installed the ubuntu 18.04 (bionic), the exim4-daemon-heavy cant start and get the error:
```

Setting up exim4-daemon-heavy (4.90.1-1ubuntu1) ...
Job for exim4.service failed because the control process exited with error code.
See "systemctl status exim4.service" and "journalctl -xe" for details.
invoke-rc.d: initscript exim4, action "start" failed.
&#9679; exim4.service - LSB: exim Mail Transport Agent
   Loaded: loaded (/etc/init.d/exim4; generated)
   Active: failed (Result: exit-code) since Thu 2018-04-12 09:15:53 +0430; 29ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 9565 ExecStart=/etc/init.d/exim4 start (code=exited, status=1/FAILURE)

Apr 12 09:15:42 myhost systemd[1]: Starting LSB: exim Mail Transport Agent...
Apr 12 09:15:43 myhost exim4[9565]:  * Starting MTA
Apr 12 09:15:53 myhost exim4[9565]: 2018-04-12 09:15:53 Malformed IP address "myhost.shams.eu.org" in local_interfaces
Apr 12 09:15:53 myhost systemd[1]: exim4.service: Control process exited, code=exited status=1
Apr 12 09:15:53 myhost systemd[1]: exim4.service: Failed with result 'exit-code'.
Apr 12 09:15:53 myhost systemd[1]: Failed to start LSB: exim Mail Transport Agent.
dpkg: error processing package exim4-daemon-heavy (--configure):
 installed exim4-daemon-heavy package post-installation script subprocess returned error exit status 1
Processing triggers for systemd (237-3ubuntu7) ...
Processing triggers for man-db (2.8.3-2) ...
Errors were encountered while processing:
 exim4-daemon-heavy
E: Sub-process /usr/bin/dpkg returned an error code (1)
Setting up exim4-daemon-heavy (4.90.1-1ubuntu1) ...
Job for exim4.service failed because the control process exited with error code.
See "systemctl status exim4.service" and "journalctl -xe" for details.
invoke-rc.d: initscript exim4, action "start" failed.
&#9679; exim4.service - LSB: exim Mail Transport Agent
   Loaded: loaded (/etc/init.d/exim4; generated)
   Active: failed (Result: exit-code) since Thu 2018-04-12 09:16:02 +0430; 28ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 10378 ExecStart=/etc/init.d/exim4 start (code=exited, status=1/FAILURE)

Apr 12 09:15:57 myhost systemd[1]: Starting LSB: exim Mail Transport Agent...
Apr 12 09:15:57 myhost exim4[10378]:  * Starting MTA
Apr 12 09:16:02 myhost exim4[10378]: 2018-04-12 09:16:02 Malformed IP address "myhost.shams.eu.org" in local_interfaces
Apr 12 09:16:02 myhost systemd[1]: exim4.service: Control process exited, code=exited status=1
Apr 12 09:16:02 myhost systemd[1]: exim4.service: Failed with result 'exit-code'.
Apr 12 09:16:02 myhost systemd[1]: Failed to start LSB: exim Mail Transport Agent.
dpkg: error processing package exim4-daemon-heavy (--configure):
 installed exim4-daemon-heavy package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 exim4-daemon-heavy

```
and this is the exim4 paniclog as well the mainlog last lines:
```

2018-04-12 09:00:34 Malformed IP address "myhost.example.com" in local_interfaces
2018-04-12 09:12:29 Malformed IP address "myhost.example.com" in local_interfaces
2018-04-12 09:15:53 Malformed IP address "myhost.example.com" in local_interfaces
2018-04-12 09:16:02 Malformed IP address "myhost.example.com" in local_interfaces
2018-04-12 09:23:00 Malformed IP address "myhost.example.com" in local_interfaces

```

---

### Post by Bashing-om on 2018-04-12
shamsat; Hello ;

I honestly really and truly do not know, as I have no experience with the app.
However. have you attempted to re-configure ?
From apt show:
> 
 To repeat the debconf-driven configuration process in a standard setup, invoke dpkg-reconfigure exim4-config. 


see if that brings in the hostname.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by shamsat on 2018-04-13
Hi Bashing-om,
Tanks for the hint the problem was with configuration file.

---

### Post by Bashing-om on 2018-04-13
shamsat; Great !

Glad you sussed it out .
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]were nothing but a thing
[/INDENT][/INDENT]

---

