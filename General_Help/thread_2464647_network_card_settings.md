---
title: "network card settings"
date: 2021-07-07
forum: General Help
---

### Post by amos76 on 2021-07-07
Newvie Installed 20.04 Ubuntu<br>I have a gigabyte lan card and by download is showing only 100 MB.&nbsp; How do I get to settings and/or install mfg driver?

---

### Post by HermanAB on 2021-07-09
It doesn&#8217;t work quite like that.

The network chip automatically negotiates the fastest speed that can be used between the two devices (computer and router).

If your new card connects at a low rate, check the other end - the router may only be 100 Mbps capable.  You may also have a bad cable - you need a CAT6 cable for GigE.

See this for details: 
[https://en.wikipedia.org/wiki/Autonegotiation](https://en.wikipedia.org/wiki/Autonegotiation)

---

### Post by The Cog on 2021-07-09
ethtool allows you to set many card settings - speed, duplex, auto-negotiation etc.
I haven't tinkered with it myself but I suspect that as HermanAB hints, the link just won't come up if you try to force it to use a speed that the other end or the cable doesn't support.

---

### Post by The Cog on 2021-07-09
ethtool allows you to set many card settings - speed, duplex, auto-negotiation etc.
I haven't tinkered with it myself but I suspect that as HermanAB hints, the link just won't come up if you try to force it to use a speed that the other end or the cable doesn't support.

---

