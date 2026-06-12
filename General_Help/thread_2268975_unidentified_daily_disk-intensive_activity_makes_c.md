---
title: "unidentified daily disk-intensive activity makes computer completely unusable"
date: 2015-03-12
forum: General Help
---

### Post by halfbeing on 2015-03-12
Since installing vanilla Ubuntu, as opposed to the UbuntuStudio I was running before, I find that at some point every day there is a long period of very intense disk activity which makes the machine so unresponsive that I can't move the mouse pointer, let alone launch iotop to find out what is causing the problem. The only way I have found to get control of my machine again has been to press the power button for 5 seconds and lose all my work. I have let this behaviour go on for as long as 50 minutes before I gave up and forced a shutdown. I have tried disabling the mlocate cron job, but that hasn't solved the problem. Does anyone know what is going on here, and how to stop it?

---

### Post by ajgreeny on 2015-03-12
It is impossible to tell you what to do as we do not know what process or processes are causing this problem.

If you can not open a terminal with Ctrl+Alt+T to run top, it might be a situation where using conky desktop monitor with "top" processes showing could help figure out what is causing the problem.  This might sound like cracking a wallnut with a sledgehammer, but it has been very useful to me in the past when I have had similar problems with a process starting and using all my cpu cycles. Unfortunately I can not now remember exactly what process it was but my conky window told me and it was easy to deal with and stop.

---

### Post by QIII on 2015-03-12
If it is something that happens at the same time daily, you could have htop and iotop running in terminals and wait to ambush it.

Next step would be logging.

---

### Post by tgalati4 on 2015-03-12
Open a terminal and check:

```
free
```  

It could simply be a RAM shortage and now swap is being used.  Quite slow indeed.

---

### Post by halfbeing on 2015-03-13
The strange thing is that it doesn't happen at the same time every day, but it does happen every day. I will try leaving iotop running in a terminal and if I can swap the windows on my desktop after the thrashing has started, maybe it will tell me something. But this seems to be something to do with vanilla Ubuntu and all the services that come installed with that, that isn't in UbuntuStudio. Is there something specific to vanilla Ubuntu and/or Unity that would periodically scan my disk?

---

