---
title: "[SOLVED] Two Instances of BIND running - don't know why"
date: 2007-11-23
forum: General Help
---

### Post by atjensen11 on 2007-11-23
I have been building a server know for the last several weeks and I have been learning a lot.  I have installed Webmin to help me administer some of the tasks, particularly monitoring the health of the server.

I am using the "System and Server Status" module within Webmin to monitor the health of my system.  It is set to email me when ever a server goes down.  Everytime I would restart my server, I noticed I kept getting a lot of emails saying the BIND server was down.

When I would type "ps -A | grep named" at a command line, I would see a process running.  In Webmin, I would browse to the BIND Server tab and see that the server wasn't started according to Webmin.  I would start the server through Webmin and retype the "ps -A | grep named" command and now see two servers named processes.

If I issue the command "/etc/init.d/bind9 stop", the first process is killed and the remaining process is the one that was started with Webmin.

I really don't know how these two items are different but was hoping someone could get me pointed in the right direction.  Do I have two BINDs installed?  How do I determine?  I do I narrow this down to only one instance?

Thanks,
Tom

---

### Post by atjensen11 on 2007-11-29
Bump -  Been a week with no replies.  I thought for sure someone would jump on this since I am willing to bet it is pretty easy.

---

### Post by atjensen11 on 2008-01-03
I discovered in the Wemin Module Configuration for the BIND DNS Server that I had to use a custom path to the PID file location. This ended up being:

```
/var/lib/named/var/run/bind/run
```

This now has Webmin reporting the BIND server status (up/down) the same as using netstat or start/stop with /etc/init.d/bind9.

---

