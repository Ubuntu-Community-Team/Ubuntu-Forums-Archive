---
title: "Desktop loosing time"
date: 2012-10-17
forum: General Help
---

### Post by niranjan_rao on 2012-10-17
This probably might be hardware issue, but my machine is slowly loosing time. Right now its behind almost by 4 minutes as compared to other machines. This impacts lot of things - especially email since I have it sorted by the date/time.

In the time & date settings, I have enabled (had always enabled) Automatically form the internet option. But seems like it does not have any impact.

Looking for solution to get my time right 

Thanks

---

### Post by niranjan_rao on 2012-10-19
I did some more research and think that this is Ubuntu problem. 

If I execute command
ntpdate ntp.ubuntu.com pool.ntp.org

machine updates to the right time and maintains the time so long as I am active on the machine. During the night when I just lock the terminal and go home, it looses the time. So something happens when the machine is idle.

---

### Post by Lars Noodén on 2012-10-19
You can set the clock once with ntpdate and then install either the package ntp or openntpd.  ntp or openntpd will automatically keep your clock in sync with networked time servers.  You only need one, but there is a choice.

(PS.  You can correct the title to 'losing' and the body to 'loses', which is the word you were looking for.)

---

