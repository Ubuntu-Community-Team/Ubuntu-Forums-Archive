---
title: "Does Ubuntu Automatically set the clock?"
date: 2008-05-31
forum: General Help
---

### Post by jras20 on 2008-05-31
I was wondering in Ubuntu does it use a server to set the clock Automatically like windows does?  Not to big of a deal if it doesnt, but just wondering.
Thanks

---

### Post by noynac on 2008-05-31
> **jras20 said:**
> I was wondering in Ubuntu does it use a server to set the clock Automatically like windows does?  Not to big of a deal if it doesnt, but just wondering.Thanks

Ubuntu will optionally set the time automatically. To enable this option:

1) right-click on the time/date in a panel;

2) select adjust date and time;

3) change the configuration option to "keep syncronized with internet servers."

You can also select *system > administration > time and date* as an alternative to 1 above.

---

### Post by jras20 on 2008-05-31
How often does the server update?

---

### Post by noynac on 2008-05-31
> **jras20 said:**
> How often does the server update?

I don't know the answer to your question. However, the time correction is done by ntp (network time protocol), and the organization that maintains this has an informational page at:

[http://www.ntp.org/ntpfaq/NTP-s-algo.htm#S-ALGO-BASIC](http://www.ntp.org/ntpfaq/NTP-s-algo.htm#S-ALGO-BASIC)

It states that:

*NTP maintains an internal clock quality indicator. If the clock seems stable, updates to the correction parameters happen less frequent. If the clock seems instable, more frequent updates are scheduled. Sometimes the update interval is also termed stiffness of the PLL, because only small changes are possible for long update intervals.*

So, it would appear that there is no specific update period, but I am by no means an expert on this. Perhaps someone else will have some information.

---

### Post by jras20 on 2008-05-31
> **noynac said:**
> I don't know the answer to your question. However, the time correction is done by ntp (network time protocol), and the organization that maintains this has an informational page at:

[http://www.ntp.org/ntpfaq/NTP-s-algo.htm#S-ALGO-BASIC](http://www.ntp.org/ntpfaq/NTP-s-algo.htm#S-ALGO-BASIC)

It states that:

*NTP maintains an internal clock quality indicator. If the clock seems stable, updates to the correction parameters happen less frequent. If the clock seems instable, more frequent updates are scheduled. Sometimes the update interval is also termed stiffness of the PLL, because only small changes are possible for long update intervals.*

So, it would appear that there is no specific update period, but I am by no means an expert on this. Perhaps someone else will have some information.

Interesting.. Thanks

---

