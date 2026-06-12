---
title: "My sweet little Iptables firewall doesn't work after kernel compile!"
date: 2006-12-16
forum: General Help
---

### Post by dennis1200 on 2006-12-16
I run both a stable 6.06 LTS and a 6.10 system, so I always have the reliable option for working (and not losing data through fiddling with system settings). In my "for fun" Edgy, I recently compiled the 2.6.19.1 kernel. They seemed to have fixed the problem with iptables modules being deselected by default. I have the iptables firewall provided at [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall), which works perfectly, but after the kernel compile not so well (at all). ](*,) 

Initially it didn't work because I didn't have iptables compiled in. Oops. That is NOT the case now. Even though the firewall seems to be running, it doesn't do its job. Ports 1-103 are closed, not stealthed (probe of ports 0-1055), the rest are stealthed. This is the same result I get if I expliclity stop the firewall service. This is not Edgy specific. Another weird thing - it also doesn't work anymore if I boot the old 2.6.17 kernel. Intially it worked fine, but after the compile, the firewall doesn't work in either the new 2.6.19 or the original 2.6.17 kernel.

I have the infamous 4318 Broadcom wireless chipset, but it is working fine (after WAY too much time poring through the forums), WEP and all. Any ideas on what the deal is?

One note - please spare me the "Linux doesn't need a firewall" lecture.:-#  I'm not disagreeing with you, just personal choice.;)

---

### Post by dennis1200 on 2006-12-21
Um, 4 days later and only 25 views?! Maybe I need to work on writing tags. Polite bump.

---

### Post by rotten777 on 2006-12-21
Download the source to the previous kernel and recompile with iptables support and see if that works.

---

### Post by dennis1200 on 2006-12-22
Iptables support is already compiled in (I did this a couple of times). Initially, before I had done that, the firewall gave errors (it tries to load a few iptables modules, ip_tables included). No errors anymore, the modules are all there.

---

### Post by hanzomon4 on 2006-12-22
Do you have a router like a little box that plugs into your phone  line and computer? also how did you set up iptables, what tool did you use?

---

### Post by dennis1200 on 2006-12-22
Here it get's a bit complicated, so I'll try to make it as clear as possible.

I have two locations with different results: home and school residences.
At home (rarely here), there is a cable router and I pick up wireless. Here, both Dapper, Edgy, and Edgy w/2.6.19 have identically working firewalls (only port 113 is closed, rest are stealthed).

Back at school, there is a DSL router (2WIRE), iptables firewall (source listed in initial post) works perfectly (ALL ports stealthed) in Dapper. In Edgy as well, but only until new kernel compile, after which both 2.6.17 AND 2.6.19 didn't stealth several of the first few dozen ports, just came up as closed.

This seems to mean the router is having an influence, but the disparate results confuse me.

---

