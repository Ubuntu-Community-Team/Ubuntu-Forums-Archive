---
title: "Dansguardian Memory usage"
date: 2007-05-23
forum: General Help
---

### Post by urukrama on 2007-05-23
I've had dansguardian + tinyproxy installed on this Ubuntu Dapper machine for quite a while now. Recently, my computer really slowed down, especially when browsing the internet. I checked what applications caused it, and noticed that dansguardian had 12 (!) entries in gnome-system-monitor (all for /usr/sbin/dansguardian), each indicating a usage of 56-58 MB RAM. This was on a fresh reboot -- the longer I keep Ubuntu running, the more entries I get for Dansguardian. Tinyproxy has a similar amount of entries, but uses hardly any RAM. 

If I try to kill some of these (dependent) entries, they just reload a few seconds later.

Is this behaviour of dansguardian normal? And what does it really indicate? It can't mean that it uses 12 x 56 MB of RAM, since I only have a 258MBs, but I have seen my RAM usage go up over the last few days and can't find anything else to account for it. A plain Openbox session on startup uses now about 120-150 MB of RAM, which is way more than it ever used before (as far as I can tell).

Could dansguardian's behaviour be the cause of my computer slowing down?

---

