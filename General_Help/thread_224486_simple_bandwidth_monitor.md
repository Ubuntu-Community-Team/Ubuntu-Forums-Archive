---
title: "simple bandwidth monitor?"
date: 2006-07-28
forum: General Help
---

### Post by LordMerlin on 2006-07-28
Hi all

I'm looking for a simple bandwidth monitor. I have setup munim, but it doesn't monitor the bandwidth on my LAN. 

What I need is something which (preferably via a web browser) can show me how much bandwidth has been used on a daily basis, weekly basis and monthly basis. Munin can only show me the network throughput which doesn't help me at this stage. 

It could / would be nice if it'll capture it to some soft of DB, like MySQL, and also if it could tell me which machine on the LAN is using what. It could be even better if I could see what protocols utilises what bandwidth. 

Any recommendations?
I tried setting up MRTG but I don't know SNMP, which I don't have time to study for at this moment. iftop works nicely, but it doesn't capture to a DB, and I need to keep my SSH window open to use it. The moment I close it, it resets, and the next time I use it all the counters begin @ 0 again

---

### Post by jordilin on 2006-07-28
I tried mrtg some time ago and it was nice. In any case, try bmon:
[http://people.suug.ch/~tgr/bmon/](http://people.suug.ch/~tgr/bmon/)
and tell us something ;)

---

