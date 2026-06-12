---
title: "Restarting a service on Ubuntu Startup (without logon)"
date: 2017-02-11
forum: General Help
---

### Post by champarando on 2017-02-11
Hi!
I have Ubuntu 16 GUI installed on a Orange Pi (Raspberry Pi-like clone mini board) which I run the program "Pi-Hole" adblocker in.
The issue with Ubuntu I'm having is that the program uses a service called "**dnsmasq**" which for some reason, WHENEVER I RESTART/SHUTDOWN and power up ubuntu back up, I ALWAYS NEED TO use PUTTY/Terminal to run the command **"sudo service dnsmasq restart"** to get that program running (I usually do it via my phone using a SSH client, the Ubuntu is on login screen asking me to put a pass, the program runs before anyways, i just need to do dnsmasq restart).

So whats a way I can automatically run a command/restart a service at Ubuntu startup? (This should be automatically exectued when Ubuntu is powered on, and I usually land on the login screen where it asks me to put a password, so 90% of the time, I wouldn't want to logon, the command should just execute automatically before logon so my program works).

Like I said, when I manually restart the service, i haven't officially logged on into the GUI session, it still asks for my password, so how can I automatically run the command to restart dnsmasq service on every reboot? Or how am I able to restart a service automatically on every reboot?
I also checked that there are run levels from 0-6 so, if I want to restart/execute a cmd just on the start (before GUI sesson/gui logon), what run level is needed and how-to?

Thanks! I'm a total newbie to linux! :)

---

### Post by TheFu on 2017-02-13
There are many different ways to accomplish this task. Because this is NOT a per-user or per-login service, you can do it is a fairly predictable manner.

The way I would do it, not necessarily the "best way", but I'm positive it will work on 16.04 (don't know about 16.10 {newer isn't always better}), is to add the following into the /etc/rc.local file before the exit at the bottom.

```
sleep 30s
/usr/sbin/service dnsmasq restart &

```
This will let other, dependent services start and *calm down* before restarting dnsmasq.  This is a workaround for something that really shouldn't be needed.  Finding the real root-cause of the problem shouldn't be THAT hard for someone with a few years of experience.

Other ways to do this would be using cron with an @reboot start.
I have suspicions that the root problem is with how long some of the pi-hole subsystems take to startup. They should wait until the core networking systems are all up and working, then start the pi-hole stuff and restart any core networking stuff, as needed post-pi-hole startup.  

You might need to extend the sleep amount. Or it might be possible to reduce it. 

It also might be possible to find the last part of the pi-hole startup and use that to restart the dnsmasq daemon.

Like I said, lots of options. There are many, many, more too.  Maybe someone else will post a better solution. I haven't learned **systemd** dependencies yet and that would be something useful to know for this type of issue.  If the pi-hole honors the systemd dependency methods, a final, excellent, solution should be possible. It is just beyond me at this point.

[https://discourse.pi-hole.net/t/dhcp-error-after-update/1331](https://discourse.pi-hole.net/t/dhcp-error-after-update/1331) says to use ```

$ pihole status
::: DNS service is NOT running
$ pihole restartdns
Job for dnsmasq.service failed.
See 'systemctl status dnsmasq.service' and 'journalctl -xn' for details.
```

---

