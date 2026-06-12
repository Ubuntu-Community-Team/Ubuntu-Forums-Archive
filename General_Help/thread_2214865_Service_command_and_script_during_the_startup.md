---
title: "Service command and script during the startup"
date: 2014-04-03
forum: General Help
---

### Post by balubeto on 2014-04-03
Hi

I discovered that the service command is used to set up, configure and control a service-command inserted in a special script. Is this true? If so, could someone explain me how to create this script and how to start it when the system is started?

Thanks

Bye

---

### Post by TheFu on 2014-04-03
"service" may or may NOT work. It depends on the manner that the packager created the start/stop/restart/status/reload methods for the daemon.

So ... if you want to make your own, then look at others - these are located in /etc/init.d/   

BTW, the release you run will have different methods as Canonical/Debian switch to systemd from upstart from the scripts in /etc/init.d/ .... I was running a 14.04 beta server last week and found a number of daemons that still had to be managed by the scripts - to the "service" and "start" and "stop" and "reload" commands most definitely ARE NOT used for everything.  Personally, I find it extremely frustrating to try "service" and find it doesn't work.

BTW - they've been pushing "service" for years by having "nag messages" in the /etc/init.d/ scripts.  Stop it already and make "service" look for scripts too.

---

