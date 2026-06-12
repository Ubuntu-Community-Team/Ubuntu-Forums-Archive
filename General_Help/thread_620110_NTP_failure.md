---
title: "NTP failure"
date: 2007-11-22
forum: General Help
---

### Post by posterboy on 2007-11-22
I am using ntpd to sync my own 7.10 box, and to serve time to 2 other machines. Under 7.04 this worked flawlessly for a long time. After upgrade to 7.10, I _sometimes_ get this: 

root@raymondjones:~# ntpq -p
ntpq: read: Connection refused

The only way to recover from this that i know of is to restart ntp. After a few minutes, it does this:

root@raymondjones:~# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+caesar.cs.wisc. 128.105.201.11   2 u   14   64  377   42.290  -18.768   1.113
*ntp-2.cns.vt.ed 198.82.247.40    2 u   11   64  377   43.092  -27.948   8.746
+otc2.psu.edu    130.207.244.240  2 u   43   64  377   48.888  -20.067   1.577

That's the normal behavior, what can be causing the "connection refused" ? 
TIA

---

### Post by misconfiguration on 2007-11-23
Well this depends on which source you're using for your master NTP server.

Sometimes the step-tickers can be set at such a high rate the source you're connecting to will refuse connection. If there are so many people requesting a heartbeat every second that can have traverse effects on the servers they host. 

Try to tweak your settings to back off a bit, only poll the information you need every 30 seconds or so. Here is some basic principals when using NTP services.

[http://support.ntp.org/bin/view/Servers/RulesOfEngagement](http://support.ntp.org/bin/view/Servers/RulesOfEngagement)

If this didn't answer your question, please repost and I'll try to help you investigate further.

---

