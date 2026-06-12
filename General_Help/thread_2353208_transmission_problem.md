---
title: "transmission problem"
date: 2017-02-19
forum: General Help
---

### Post by jgw on 2017-02-19
I am running with ubuntu 16.04  I decided to run the following:
sudo apt update
sudo apt upgrade

Both had problems with transmission.  I then ran sudo aptitude update (sometimes the aptitude helps).  Same problems.

The following are some of the things I tried to see what was going on.

```

greg@greg-movies:~$ sudo service transmission-daemon status
[sudo] password for greg: 
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; ven
   Active: failed (Result: exit-code) since Sun 2017-02-19 16:30:36 PST; 34min a
  Process: 3890 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exit
 Main PID: 3890 (code=exited, status=217/USER)

Feb 19 16:30:36 greg-movies systemd[1]: Starting Transmission BitTorrent Daemon.
Feb 19 16:30:36 greg-movies systemd[1]: transmission-daemon.service: Main proces
Feb 19 16:30:36 greg-movies systemd[1]: Failed to start Transmission BitTorrent 
Feb 19 16:30:36 greg-movies systemd[1]: transmission-daemon.service: Unit entere
Feb 19 16:30:36 greg-movies systemd[1]: transmission-daemon.service: Failed with
Feb 19 16:31:00 greg-movies systemd[1]: Stopped Transmission BitTorrent Daemon.
...skipping...
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; ven
   Active: failed (Result: exit-code) since Sun 2017-02-19 16:30:36 PST; 34min a
  Process: 3890 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exit
 Main PID: 3890 (code=exited, status=217/USER)

Feb 19 16:30:36 greg-movies systemd[1]: Starting Transmission BitTorrent Daemon.
Feb 19 16:30:36 greg-movies systemd[1]: transmission-daemon.service: Main proces
Feb 19 16:30:36 greg-movies systemd[1]: Failed to start Transmission BitTorrent 
Feb 19 16:30:36 greg-movies systemd[1]: transmission-daemon.service: Unit entere
Feb 19 16:30:36 greg-movies systemd[1]: transmission-daemon.service: Failed with
Feb 19 16:31:00 greg-movies systemd[1]: Stopped Transmission BitTorrent Daemon.
~

greg@greg-movies:~$ sudo service transmission-daemon stop
greg@greg-movies:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up transmission-daemon (2.92-1ubuntu1~16.10.1) ...
Job for transmission-daemon.service failed because the control process exited with error code. See "systemctl status transmission-daemon.service" and "journalctl -xe" for details.
invoke-rc.d: initscript transmission-daemon, action "start" failed.
dpkg: error processing package transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

greg@greg-movies:~$ systemctl status transmission-daemon.service
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2017-02-19 17:05:25 PST; 2min 45s ago
  Process: 8942 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=217/USER)
 Main PID: 8942 (code=exited, status=217/USER)

Feb 19 17:05:25 greg-movies systemd[1]: Starting Transmission BitTorrent Daemon...
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Main process exited, code=exited, status=217/US
Feb 19 17:05:25 greg-movies systemd[1]: Failed to start Transmission BitTorrent Daemon.
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Unit entered failed state.
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Failed with result 'exit-code'.
...skipping...
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2017-02-19 17:05:25 PST; 2min 45s ago
  Process: 8942 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=217/USER)
 Main PID: 8942 (code=exited, status=217/USER)

Feb 19 17:05:25 greg-movies systemd[1]: Starting Transmission BitTorrent Daemon...
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Main process exited, code=exited, status=217/US
Feb 19 17:05:25 greg-movies systemd[1]: Failed to start Transmission BitTorrent Daemon.
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Unit entered failed state.
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Failed with result 'exit-code'.
...skipping...

&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2017-02-19 17:05:25 PST; 2min 45s ago
  Process: 8942 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=217/USER)
 Main PID: 8942 (code=exited, status=217/USER)

Feb 19 17:05:25 greg-movies systemd[1]: Starting Transmission BitTorrent Daemon...
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Main process exited, code=exited, status=217/US
Feb 19 17:05:25 greg-movies systemd[1]: Failed to start Transmission BitTorrent Daemon.
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Unit entered failed state.
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Failed with result 'exit-code'.
~

greg@greg-movies:~$ journalctl -xe
-- Subject: Process /usr/bin/transmission-daemon could not be executed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- The process /usr/bin/transmission-daemon could not be executed and failed.
-- 
-- The error number returned by this process is 3.
Feb 19 17:05:25 greg-movies systemd[1]: Starting Transmission BitTorrent Daemon...
-- Subject: Unit transmission-daemon.service has begun start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit transmission-daemon.service has begun starting up.
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Main process exited, code=exited, status=217/USER
Feb 19 17:05:25 greg-movies systemd[1]: Failed to start Transmission BitTorrent Daemon.
-- Subject: Unit transmission-daemon.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit transmission-daemon.service has failed.
-- 
-- The result is failed.
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Unit entered failed state.
Feb 19 17:05:25 greg-movies systemd[1]: transmission-daemon.service: Failed with result 'exit-code'.
Feb 19 17:05:27 greg-movies sudo[8832]: pam_unix(sudo:session): session closed for user root
Feb 19 17:06:18 greg-movies gnome-session[1669]: 2017-02-19 17:06:18,277::DEBUG::[interface:523] API-call from 127.0.0.1 [Sonarr/2.0.0.4472
Feb 19 17:06:18 greg-movies gnome-session[1669]: 2017-02-19 17:06:18,285::DEBUG::[interface:523] API-call from 127.0.0.1 [Sonarr/2.0.0.4472
Feb 19 17:06:27 greg-movies kernel: [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:40:8b:07:6a:e5:e0:08:00 SRC=192.168.0.1 DST=224.0.0.1 LE
Feb 19 17:07:48 greg-movies gnome-session[1669]: 2017-02-19 17:07:48,386::DEBUG::[interface:523] API-call from 127.0.0.1 [Sonarr/2.0.0.4472
Feb 19 17:07:48 greg-movies gnome-session[1669]: 2017-02-19 17:07:48,390::DEBUG::[interface:523] API-call from 127.0.0.1 [Sonarr/2.0.0.4472
Feb 19 17:08:32 greg-movies kernel: [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:40:8b:07:6a:e5:e0:08:00 SRC=192.168.0.1 DST=224.0.0.1 LE
Feb 19 17:08:37 greg-movies AptDaemon[6649]: INFO: Quitting due to inactivity
Feb 19 17:08:37 greg-movies AptDaemon[6649]: INFO: Quitting was requested
Feb 19 17:08:37 greg-movies org.debian.apt[858]: 17:08:37 AptDaemon [INFO]: Quitting due to inactivity
Feb 19 17:08:37 greg-movies org.debian.apt[858]: 17:08:37 AptDaemon [INFO]: Quitting was requested
Feb 19 17:09:18 greg-movies gnome-session[1669]: 2017-02-19 17:09:18,586::DEBUG::[interface:523] API-call from 127.0.0.1 [Sonarr/2.0.0.4472
Feb 19 17:09:18 greg-movies gnome-session[1669]: 2017-02-19 17:09:18,591::DEBUG::[interface:523] API-call from 127.0.0.1 [Sonarr/2.0.0.4472
Feb 19 17:10:37 greg-movies kernel: [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:40:8b:07:6a:e5:e0:08:00 SRC=192.168.0.1 DST=224.0.0.1 LE
Feb 19 17:10:48 greg-movies gnome-session[1669]: 2017-02-19 17:10:48,681::DEBUG::[interface:523] API-call from 127.0.0.1 [Sonarr/2.0.0.4472
Feb 19 17:10:48 greg-movies gnome-session[1669]: 2017-02-19 17:10:48,687::DEBUG::[interface:523] API-call from 127.0.0.1 [Sonarr/2.0.0.4472
Feb 19 17:10:59 greg-movies org.gnome.zeitgeist.SimpleIndexer[1570]: ** (zeitgeist-fts:2105): WARNING **: Unable to get info on application
lines 1106-1146/1146 (END)
[
```

As you can see I have problems.  My thought is to remove and re-install the transmission daemon but thought I had better ask what others think before I really screw it all up.

Thank you...........

---

### Post by HereInOz on 2017-02-20
I tend to agree.  
Run 
sudo apt-get purge transmission* 
to remove any software starting with "transmission" 
Then 
sudo apt-get autoclean
and 
sudo apt-get autoremove 
just to be sure.

Then re-install Transmission.

After that, I am as clueless as can be.

---

### Post by jgw on 2017-02-21
Thank you for the reply.

I rooted about on this and found that there is a question as to whether I should use the apt-get command with 16.04   (apt get purge transmission-daemon)  I currently have plain transmission and transmission-daemon.  Its the daemon that is giving me problems.  I use the vanilla version for manual downloads and the daemon for sonarr.  so, are you sure the apt-get will get the job done using 16.04

Should mention that its kinda tough to figure out what works with what with ubuntu and, when rooting about for answers, there are always 3 or 4 suggested and one never knows what applies.  

Thanks again!

---

### Post by wildmanne39 on 2017-02-21
It is supposed to be:
```
sudo apt update
```
in 16.04 and beyond, I recently helped a user not being able to update and I discovered that the old command:
```
sudo apt-get upgrade
```
this is just an example for purposes of syntax, can actually break the package management, so I am changing to the new commands from now on.

---

### Post by jgw on 2017-02-22
Thank you!

I did as you suggested and it worked flawlessly!  Its up and running and we will see how it works.

Thanks again!  (I will mark this one solved)

---

### Post by wildmanne39 on 2017-02-22
Your welcome!
Enjoy!

---

