---
title: "NAT masquerade problem"
date: 2007-03-20
forum: General Help
---

### Post by rhn on 2007-03-20
Hi

I am having problems setting up NAT with iptables.
First, I have tried to define my own rules using this as reference:

[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

After many unsuccesful tries, I have decided to run the original script from [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES)

but still, the firewall doesn't work.

I have noticed that the gateway computer doesn't forward anything even with the most liberal options enabled - all packets that ask for external IPs are dropped.

I have Edgy with 2.6.17-11 kernel.

Please help!

---

### Post by kidders on 2007-03-20
Hi there and welcome,

> **rhn said:**
> I have noticed that the gateway computer doesn't forward anything even with the most liberal options enabledDid you remember to enable packet forwarding?

Also, could you describe what you want your router to do, exactly. I took a cursory look at the other thread you mentioned in your o/p, and it seems to describe the procedure for doing things like having a DHCP server listen on multiple interfaces, which may not always be appropriate. The reason I ask is that, a lot of the time, routers connect LANs to the internet (rather than LANs to eachother), so you would want as little as possible going on on an external interface.

---

