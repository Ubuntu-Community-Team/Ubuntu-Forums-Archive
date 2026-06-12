---
title: "Firewall question"
date: 2005-08-24
forum: General Help
---

### Post by MdaG on 2005-08-24
What would you recommend a n00b like me to use as a firewall. I have little knowledge of iptables and I need to allow echo requests from my ISP to be able to access the internet. In XP I used ZoneAlarm. I need something that'll keep my box safe and at the same time be easy to use. I know that iptables is easy to use once you know how to use it, but I don't have time to delve into all those docs...

---

### Post by heimo on 2005-08-24
I'm not too familiar with [firestarter]("http://packages.ubuntu.com/hoary/admin/firestarter") and what you can do with it, but if you haven't seen it yet, do. :)

---

### Post by MdaG on 2005-08-24
Firestarter uses iptables. Are the neccesary modules compiled in the kernel as default? It doesn't seem to find ip_conntrack among others... also even though I've set the policy to allow traffic from a certain IP it keeps blocking them...

---

