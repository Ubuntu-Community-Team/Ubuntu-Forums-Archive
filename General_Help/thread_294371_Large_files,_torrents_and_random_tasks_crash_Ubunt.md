---
title: "Large files, torrents and random tasks crash Ubuntu (edgy)"
date: 2006-11-06
forum: General Help
---

### Post by ChibiArt on 2006-11-06
:S

any ideas?

torrents, large files (as in, downloads) and random tasks crash my ubuntu installation - obiously, essential featres.

anyone had a simular problem? how did you fix it

---

### Post by PriceChild on 2006-11-06
The fact that they're random doesn't help people troubleshoot your problem.

Could you maybe check your system logs to see what comes up around the time of the crashes.

What type of crashes are these? Hard locks? X crashes... etc. etc. ?

---

### Post by ChibiArt on 2006-11-06
ubuntu newbie.. how do I get to system logs?

and the whole system comes to a standstill and I have to press the power btton on the PC to put it off&back on

---

### Post by ChibiArt on 2006-11-06
i've found netbased things are crashing me..
..something to do with ndiswrapper?

---

### Post by hikaricore on 2006-11-06
Your log files are located under /var/log

Some you may want to look into for info are:

messages
kern.log
syslog

Now the info in there might look a bit scary but it's all time stamped and it may give you an idea of what happened if you look closely.

Another one you probably should look into is .xsession-errors in your root directory.  This is usually full of junk that won't be of much use but sometimes it can help.  As far as other applications, some keep logs and some don't.  If you're noticing crashes revolving around a few specific apps, check to see if they're keeping logs of their activity.

---

### Post by ChibiArt on 2006-11-10
Sorry for the delay, i've been trying it with other distros but I can't even get as far as connecting to the internet on them!

What i'm seeing from another thread is i'm not the only one getting this lockup with the NETGEAR WG111v2.

Anyone found a solution? It uses the rtl8187 WIRELESS LAN driver for native linux but i'm using it with ndiswrapper using the tutorial on this website somewhere.

So yeah - any ideas?!

---

### Post by n8bounds on 2006-11-19
Remove the offending hardware and see if the symptoms stop.  If they do, don't put it back in and go get something else!  :)

---

