---
title: "autostart services with proxychain"
date: 2012-11-19
forum: General Help
---

### Post by arbiter2x on 2012-11-19
hi,
I'm running a ubuntu server on a machine, that has sabnzbd installed.
however, I need to reroute all the connections through a http proxy.
usually i do that with the command "proxychains sabnzbdplus"

but I want sab to autostart as a service when I boot the machine.
how can I change the regular sabnzbdplus service so it ALWAYS stars via proxychains?

I've already tried to edit the sabnzbdplus-file in /etc/init.d/
however I'm not sure which line to change...

is there a general approach on how to change the service startup-command of applications?

---

