---
title: "iptables dnat question"
date: 2008-01-08
forum: General Help
---

### Post by dr_d on 2008-01-08
Okay here's the deal: I'm adding iptables rules to my nat router (10.0.0.1).

I want to redirect all traffic coming from a rogue host (10.0.0.8) to the IP of a webserver which basically tells the mofo off for using my network. Grrrrr.


For example:
iptables -t nat -I PREROUTING -s 10.0.0.8 -j DNAT --to 64.111.96.38
That works fine. Redirects everything coming from the rogue host (10.0.0.8) to kittenwar.com

Now if I replace the kittenwar.com IP with 10.0.0.1 (my nat router), then if I try to browse the net from the rogue host, I see the config page for my nat router. Fine. No problems there.


Here's the problem: if I set up the rule so that it redirects everything to an INTERNAL address other than my nat router, I just get timed out.

I've got a (working) webserver on 10.0.0.3.
iptables -t nat -I PREROUTING -s 10.0.0.8 -j DNAT --to 10.0.0.3
Now if I try to browse the net from the rouge host, it just times out.


Does anybody know why this might be happening?

---

### Post by dr_d on 2008-01-08
anybody? anybody? bueller? bueller?

---

