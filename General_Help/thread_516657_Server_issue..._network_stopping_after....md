---
title: "Server issue... network stopping after..."
date: 2007-08-03
forum: General Help
---

### Post by siafulinux on 2007-08-03
[SIZE="3"]Okay, hi guys and gals.

Wasn't exactly sure where to place this one as I'm not sure if it's a hardware or software issue.

I have two servers running in my home for basic web serving and Intranet / proxy / filtering. Both were on Ubuntu server editions, but recently switched one to Debian in an attempt to overcome a small, but aggravating issue I seem to be having.

On the originally Ubuntu, but now Debian server networking will just stop. I'm not exactly sure why. If there is little activity the server stays up for days, no problem. Then if there is a bunch of activity (so it seems) the server just stops. Everything is responsive from a log in and work in the system point of view, but networking will be dead. 

On the Intranet / Filter set up, the Ubuntu system works just fine, but if I try to use dansguardian, it slows down HEAVILY. I have only two active machines routing through it. So I'm stumped. Then, after a certain amount of activity it seems as though it just stops filtering / forwarding. Network issue or a dansguardian issue?

So, all in all, I am stumped about this. Is it perhaps bad network cards or perhaps a config error? Any ideas would be appreciated as I am trying to spread the benefit of using Linux (Ubuntu / Debian) over Windows and yet my systems are continuously being rebooted. And of course it's just irritating! :-)

Specs:

**_Web Server Machine_**
Processor: 650mhz PIII
Mem: 131mb

**_Intranet / Filter Machine_**
Processor: 788 mhz PII
Mem: 65mb


Side note: I should probably put the server on the 788 machine!  ;-)

Thanks! Siafu[/SIZE]

---

### Post by siafulinux on 2007-08-04
[SIZE="3"]Okay I think I figured out the Intranet / Filter. I think the virus scanning with dansguardian was a bit much for the system. So I disabled it. I also am using squid-proxy as apposed to tinyproxy and also put a dns server on it.

So far it all seems to be working well!

Still, the web server that just stops networking after a while? Any ideas will be appreciated.

Siafu[/SIZE]

---

### Post by siafulinux on 2007-08-04
[SIZE="3"]
Okay this time the server went down and the entire thing froze... I can't see this as being a bad network card? Maybe it's a memory module...?

Anyway, thanks for all the help. 
[/SIZE]

---

