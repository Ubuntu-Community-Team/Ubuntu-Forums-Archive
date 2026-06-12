---
title: "Ubuntu phone home?"
date: 2013-06-24
forum: General Help
---

### Post by t0p on 2013-06-24
Why is my computer calling Canonical?

*excerpt from* **netstat -tcp**
```

tcp        0      0 mars.local:55162        grape.canonical.c:https ESTABLISHED 2381/python     
tcp        1      0 mars.local:55465        mulberry.canonical:http CLOSE_WAIT  2080/ubuntu-geoip-p

```

I get the ubuntu-geoip-p thing - my computer is telling Canonical where I am.  Understood, but not happy.  How do I get Canonical to quit keeping tabs on my location?  And it's not even https!  Anyone could intercept it!  It's not like I'm a secret agent or on the run from the law or something... but I *could* be.  What happened to *privacy* (yeah I know "privacy is dead" etc but Canonical could at least *pretend*.  Folk go on about how Linux is so much more secure - and then this.  And I know I'm talking about privacy and security as if they were the same thing, but they are sometimes)? And the thing that grape.canonical thing is doing, that python thing... what's *that* all about?

Not happy.

---

### Post by 3rdalbum on 2013-06-24
One connection is periodically confirming your time zone so the clock can be synced. The other gets your location so the Videos lens can show you only the video sources you can actually use. (e.g. You wont see BBC videos outside the UK).

Unless you have a GPS transciever in your computer, the location fix will be limited to knowing what city you are in. I don't think it gets down to suburb-level accuracy, much less street level.

You can redirect these IP addresses to a nonexistent location in your /etc/hosts file if you want, but it is all pretty harmless, and just being helpful.

---

### Post by Mark Phelps on 2013-06-24
A common  misperception, caused mostly by the major media's penchant for spreading fear and dread, is that if someone has your IP address, they can find your location -- down to the street address, apartment number, etc.

This is simply NOT true.

If you're connected to an ISP to get internet access, they have a DHCP server that issues you an IP address -- from  the pool that they are allowed to manage. When you do a WhoIS against that IP, you do NOT get your home address (if you are at home now).

I just checked to confirm this with my IP address, used four different IP address search apps, and in NO case, was the address reported anywhere near where I am currently.

So, folks, if you're worried about folks breaking down your door -- based solely on your IP address -- then you need to quit watching so many movies.

---

