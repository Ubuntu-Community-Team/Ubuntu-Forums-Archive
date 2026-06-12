---
title: "GDesklets + SideCandy Massive Ram Usage"
date: 2008-02-21
forum: General Help
---

### Post by spooner on 2008-02-21
OK, So my PC has been on for 6 days and now GDesklets is using 1.3 Gb of RAM. By "use" I mean using (not cache or anything).
I'm running Ubuntu 7.10 (Gusty) on a P4 Dual with 2Gb so when Gdesklets uses over half I have a problem. I have some side candy desklets that show CPU, RAM, HDD, Network etc) & I was just wondering if anyone else has had a similar problem. 
I'm currently running a Matlab script (which is only using 40Mb RAM by the way) but is very processor intensive (which is why my PC has been on for 6 days).
First I tried restarting all the desklet but this had no impact.
I've tried closing all the open desklets  but
"python /usr/lib/gdesklets/gdesklets-daemon" is still using 1.3GB of RAM...
Only thing left was to kill gdesklet-daemon and start it again which returned all my ram (everything now using only 380MB).

What I really want to know is has anyone else noticed anything similar and what do you think would happen if I hadn't killed it and it continued to eat RAM?

---

