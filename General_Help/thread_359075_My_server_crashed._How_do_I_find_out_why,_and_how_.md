---
title: "My server crashed. How do I find out why, and how can I recover some lost data?"
date: 2007-02-11
forum: General Help
---

### Post by Adam Atlas on 2007-02-11
A few days ago my colocated server running Ubuntu Edgy (under Xen) went down. I quickly called my ISP and they rebooted it, but I still have not been able to find anything explaining the cause of the crash. I've looked in all the usual /var/log files, and I don't see anything that seems relevant. Where else should I look?

Also, just today, I noticed some files were gone. I hadn't been working with them at the time of the crash, but I guess it's something to do with the filesystem being unmounted forcefully when the server was rebooted. Is there any hope of recovering them? Where could I start?

---

### Post by shareMenaPeace on 2007-02-11
Hi for logs i use
System -> Administration -> System Logs 
Not sure if those logs origin is in /var/logs

---

### Post by Adam Atlas on 2007-02-11
This is a server... I don't have the desktop packages installed, I'm working remotely with a command line.

---

