---
title: "Can I have both ethernet and WiFi active?"
date: 2005-10-28
forum: General Help
---

### Post by ordered_chaos on 2005-10-28
I followed the Ubuntu WiFi doc to a T and got my WiFi working! The guide deactivate all other network devices to get the WiFI working, so does that mean I can't have a simultaneous WiFI and Ethernet connection? My Ethernet connection is not DHCP and all computers that are connected to it have static IP address. 

Why do I want this dual connection? 1) Fast 100 m/bit file transfers, 2) Ubuntu net installer! Thanks for anyone who help me or tell me how to get both WiFi and ethernet working.

---

### Post by mlomker on 2005-10-28
I'm not sure what doc you used.  You can have multiple network interfaces but only one default route (unless you adjust the metrics).  In other words, you're only going to have one connection to the Internet and the other connection would have to be to local machines.

---

### Post by cbudden on 2005-10-28
When I have had both on i cannot connect to the internet.  If I disable one then everything is ok.

---

### Post by TimelessRogue on 2005-10-28
Yes, you can have both active.  However, only the "Default gateway device" will be available for internet access.  You can set the default device ... eth0 or eth1, for instance ...  with System/Adminstration/Networking.

---

