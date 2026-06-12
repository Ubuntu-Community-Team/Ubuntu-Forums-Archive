---
title: "is there an ISA server remplace?"
date: 2006-11-02
forum: General Help
---

### Post by damvcoool on 2006-11-02
ok this is really a question, you can move this where ever is apropiate.

is there any Linux solution that does what and M$ ISA server does??

i ask this question because i am currently studying for NETWORK ADMINISTRATOR, and right now we are over the ISA SERVER, but when i ask my teacher he said he did not know if there was any integrated solution like that for Linux, i know that there are different application that do the same but they are separated. well if you guys know any integrated solution, or at least a how-to to put a proxy, firewall, web-caching,VPN, and Routing and Remote Access server, all-in-one please tell me.

Thank you :D

---

### Post by dro0g on 2006-11-02
Yes, there are packages that cover those functions in Linux - Squid for proxy and caching, IPTables for firewall, PoPToP or openvpn for VPN. 

Keep in mind that in the RealWorld(tm) no one actually uses ISA - Cisco, Checkpoint, Juniper, etc DOMINATE in this space. ISA is one of the few apps where the "no one gets fired for using Microsoft" thing doesn't hold true.

---

### Post by damvcoool on 2006-11-07
ok thank you i will use this as my base:

Squid, IPtables (with any of their interfaces), and openvnp. :D

---

