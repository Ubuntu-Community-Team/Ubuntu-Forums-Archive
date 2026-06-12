---
title: "Router Traffic Monitor"
date: 2022-04-26
forum: General Help
---

### Post by wjbmd48 on 2022-04-26
I have a dumb question about monitoring my traffic at the router/IP level. I recently "upgraded" my router from an TPLink Archer 7, which had a traffic statistics function, to an Archer 8, which doesn't.

Is there a simple traffic monitoring app that will do the same thing at the router level (and not just for the traffic on my PC)? I've installed darkstat, but can't figure out how to fire it up.

Thanks!

Bill

---

### Post by TheFu on 2022-04-27
No.

Traffic can only be monitored if it traverses the system where the monitoring happens.  That's the nature of a switched network. Only the specific devices involved see the traffic.  It is also a security thing.

However, you may be able to install a monitoring tool on the router which sends data to another system. I highly doubt any consumer router would support this. It is key reason why I stopped the consumer router 3-5 yr upgrade cycle and got a purpose-built x64 mini-PC to be the WAN router here. It runs opnsense, but it can run pfsense or open-wrt or a custom Linux easily.  Inside opnsense, the monitoring is great and it can also send snmp data to another device on the network for more graphing. I've had this purpose-created PC for about 6 yrs now and it got patched Friday. I expect it will continue to work for 10+ more years.  Not bad for $144 total in 2015.  It doesn't have wifi, but connecting a wifi-AP is trivial - plus the FBI says all wifi and IoS stuff should be on different subnets for security reasons, which this network design supports. As wifi standards change, a new AP can be bought to keep up, but the router doesn't need to be reconfigured completely.

I have a rule for all routers. If they haven't been patched in the last 3 months, then they aren't actually supported and need to be replaced. The world is just too dangerous without properly maintained router software on the internet. Every month, we learn about some other remote-take-over of routers somewhere in the world.  BTW, I had a TP-link router before switching. It was full of bugs and they only put out fixes a few times a year, and they only did that for a few years from when it was new.  

I have a dumb tp-link switch too. It doesn't get any updates and because it is a dumb switch, I don't expect it to ever need any updates. I'm extremely happy with it.  It provides a physical separate network for some of my systems from other subnets off that fancy router. The router controls security between the different subnets.

---

### Post by wjbmd48 on 2022-04-27
Thanks!   That's greatly appreciated.

Bill

---

