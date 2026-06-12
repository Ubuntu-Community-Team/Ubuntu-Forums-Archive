---
title: "Linksys WRT45G Version 8.0 not working"
date: 2008-04-05
forum: General Help
---

### Post by CD27 on 2008-04-05
Alright, finally got my internet working on my linux box. Unfortunately, my windows box has Safe eyes on it and it won't allow me to hook up wireless (wtc), oh well. I can bypass it if i set it up on the linux box and use the router as a switch. Here's the deal. I don't have the setup cd. So, i hook it up like i'm sposed to, but it won't go on. I even try to connect to 192.168.1.1, but nothing at all. What am i missing here?

cd

---

### Post by dstew on 2008-04-05
> I even try to connect to 192.168.1.1, but nothing at all. What am i missing here?Maybe your Ubuntu system does not have TCP/IP set up. If the router is not set up as a DHCP server, but your Ubuntu settings are for DHCP, you might not have an IP address, so you cannot get the requested web setup page. Please post the output of```
ifconfig
```Also, look how your Windows side is connecting to the router. Does it use DHCP, or have a static IP address?

---

### Post by danwood76 on 2008-04-05
The router IP may be something different like 10.0.0.1
Have a look on the linksys site for a manual and do a full reset of the router (the little button on the back for 5 seconds or so), then try to connect it up.

---

