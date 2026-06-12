---
title: "I can SSH to a ubunto system from one IP in my network but not another"
date: 2014-06-30
forum: General Help
---

### Post by duane6 on 2014-06-30
I have a Ubuntu system in a network segment 10.15.82.20.  I can ssh to this machine from my ip 192.168.0.156 (W7) but not 192.168.0.246 (Ubuntu system).  Both 192.168.0.100 and 192.168.0.146 are in the same network.

But from the 192.168.0.246 Ubuntu machine I can ssh to any of the 28 others I have in different network segments.  I was able to ssh to the 10.15.82.20 originally but now I cannot.

From:  192.168.0.100 W7 using putty
ssh 10.15.82.20
This works to this device and any I have in other network segments

From 192.168.0.146 ubunto using ssh from terminal window
ssh 10.15.82.20
This has quit working in the past week, connection closed.  This did work and I can ssh into 27 other boxes that are clones, just different IPs and different network segments.  I can ping and traceroute to the ip.



Rebooted both 192.168.0.146 and 10.15.82.20, rebooted firewall on the remote network connection, rebooted switch.    Make no sense.

I am a ubunto rookie and am stuck on where to look.  Any help is greatly appreciated!!


Thanks,
Duane

---

### Post by duane6 on 2014-06-30
Well, I may have found the issue.  Looks like the connections between these two devices were not dropping.  Found by looking at firewall.  When I unplugged the 10.15.82.20 device from the network for a few minutes and let all the showing active connections drop (that were showing in the firewall monitor, I able to put the device back on the network and then ssh to it.

---

