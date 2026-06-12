---
title: "[SOLVED] Printing Not working on this fresh FF 7.04 system"
date: 2007-07-23
forum: General Help
---

### Post by Gruelius on 2007-07-23
Hey everyone. Unfortunately i have no other linux system to test this on but with my other FF Kubuntu pc printing via IPP to my ubuntu server running cups worked fine.

On my new client machine it does not print to my server. I get told that the jobs are stopped or stopped indefinately and this is my error log.

 [23/Jul/2007:18:00:58 +1000] PID 5382 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
E [23/Jul/2007:18:00:59 +1000] PID 5383 (/usr/lib/cups/backend/http) stopped with status 1!
E [23/Jul/2007:18:01:16 +1000] PID 5448 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
E [23/Jul/2007:18:01:17 +1000] PID 5449 (/usr/lib/cups/backend/http) stopped with status 1!
E [23/Jul/2007:18:01:28 +1000] PID 5499 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
E [23/Jul/2007:18:01:28 +1000] PID 5500 (/usr/lib/cups/backend/http) stopped with status 1!

I am clueless about what i need to do. What does status 1 mean? My network is a bit sketchy (FF + rt2500) however all applications so far can use the web and i have an IP assigned e.t.c.

Thanks
Julius

---

### Post by Gruelius on 2007-07-23
SOLVED

I found out i needed to install a printer driver not just use the PPD on its own, even when the printer is on a CUPS server.

---

