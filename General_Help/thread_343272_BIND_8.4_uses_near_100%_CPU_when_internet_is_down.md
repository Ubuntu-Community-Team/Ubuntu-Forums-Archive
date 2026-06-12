---
title: "BIND 8.4 uses near 100% CPU when internet is down"
date: 2007-01-21
forum: General Help
---

### Post by rogblake on 2007-01-21
I'm running BIND 8.4.6 on my Dapper system, for caching internet DNS requests as well as providing DNS for the local network.

Internet access is via dialup. What is occuring is that when the internet is down, the named daemon after a while (maybe an hour or two) will start chewing up nearly 100% of the CPU.  This continues until it is killed off or the internet is dialed up. Once the internet is connected, the named daemon drops to normal CPU utilization levels within seconds. There are no named diagnostics to be found in /var/log/messages.

I've done some searching with Google and found a lot of references to CPU utilization problems in named, but have not found anything yet relating it to whether or not the internet is connected. Is this a bug? A configuration problem? Will updating to bind 9 be of any help?

---

### Post by humphry on 2007-03-14
I have a similar problem, but with some differences.  I don't have BIND, and I'm pretty much using Ubuntu out of the box.  I usually have wireless internet all the time, but I don't for this one week.  I've found that if I turn on my computer and I'm not connected to the router, my processor runs at 50%.  Plugging into the router makes it go to normal levels.  It remains at normal levels even if I unplug immediately after.  Have you found anything to deal with this?

---

