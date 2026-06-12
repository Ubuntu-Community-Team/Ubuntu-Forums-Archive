---
title: "clock problem"
date: 2004-11-07
forum: General Help
---

### Post by rottame on 2004-11-07
Hi
I've just installed ubuntu on an old k6/2 400MHz, Asus P5A motherboard.
With the default 2.6.8 kernel one minute is long at least three real minutes(sleep 1 sleeps 3-5 seconds) and everithing is slow, the logs are full of this warnings:
  Losing some thicks.... checking if CPU frequency changed.
With 2.6.7 one minute is long something like 20-25 seconds (everithing runs faaaast for an old k6/2 :) ), no warnings.
I'm really lost.
Someone can tell me wich patch, kernel configure option can cause this behaviour?

---

### Post by mercurus on 2004-11-08
Have you tried using a K6-specific kernel image ? Alternatively, you could upgrade to 2.6.9 and hope for the best ...

Is this a laptop ? If so, check your ACPI and APM settings to see if the processor is scaling on battery power and messing with the clock voltages accordingly ... Even if it isn't a laptop try and disable ACPI and APM and see if timekeeping improves.

Finally, if that's too hard, re-configure ntp to synchronise VERY regularly with another machine on the LAN or on the Internet. That way you should be able to keep time slightly better ... but a kernel fix would be preferable.

Cheers
mercurus

---

### Post by rottame on 2004-11-08
I'm only a stupid lamer :)
acpi=off did the trick.
Probably the problem is one of the patches ubuntu uses, because a stock 2.6.x works with acpi enabled.
with or without acpi doesn't matter, this is only a secondary box, a web/sql server only for testing web pages.

Thanks

---

