---
title: "problems with network (DNS/Firestarter)"
date: 2007-08-13
forum: General Help
---

### Post by john_brown_jr on 2007-08-13
Hello folks,

I'm running a small home server with PHP/Apache + DNS server + Firestarter as firewall. It has recently come to my attention that ~ 80% of my visitors can not access my site. It seems that customers from one of the countries largest ISP (Apollo) are mostly affected.

Some users report that domain name can't be resolved, while for others DNS is working, but they simply can not connect. Google/Yahoo/other crawlers somehow manage to index my site successfully. Does anyone have any idea on what might be wrong and how to debug it?

1) My first idea was that I have somehow misconfigured Firestarter. /var/log/messages contained information about failed domain name transfers (IP address was my top-level DNS server, port=DPT=53). I have opened (among others) ports 80/53, so I have no idea on how this message could have appeared in the logs.

2) Maybe my ISP selectively blocks some packets from certain ISPs? If so, how can I debug this?

Any hints/ideas would be greatly appreciated.

SOLVED:
Secondary DNS server was dead, and some clients still somehow tried to connect to it, and failed. Updated records for secondary server (also got registar to do the same), and everything seems to be fine now.

---

