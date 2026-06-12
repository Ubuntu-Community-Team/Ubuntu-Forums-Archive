---
title: "startxfce4.log filling disk, log does not indicate why."
date: 2014-03-31
forum: General Help
---

### Post by grout5811 on 2014-03-31
The log file at ~/.cache/upstart/startxfce4.log is filling up my hard disk with in days growing gigs in size.  The log file contains nothing but ip addresses.  I put a link to a pastbin with part of the log in it.  

[http://pastebin.com/zU6c52lh](http://pastebin.com/zU6c52lh)

---

### Post by grout5811 on 2014-03-31
I figured it out, appears vino-server was getting hammered on by requests and logging it in that log file.

---

