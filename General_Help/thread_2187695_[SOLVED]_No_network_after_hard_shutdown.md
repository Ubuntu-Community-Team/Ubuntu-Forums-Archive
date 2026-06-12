---
title: "[SOLVED] No network after hard shutdown"
date: 2013-11-13
forum: General Help
---

### Post by Jigsaw52 on 2013-11-13
Hi

I have a laptop with Xubuntu 13.04 and I use wicd to connect to the Internet.
This morning there was a power failure and I didn't have my battery connected so my laptop turned off. Upon rebooting, I was unable to access the Internet even though I was able to access my router configuration page. This happens both with wireless and wired connections.

Pinging 8.8.8.8 results in:
> connect: Network is Unreachable

The route command gives me the following output:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0    *               255.255.255.0   U     0      0        0 wlan0


After running the following command:
> 
sudo route add default gw 192.168.1.1 wlan0


I was able to restore network connectivity. And now route gives me the following output:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1          0.0.0.0         UG    0      0        0 wlan0
192.168.1.0    *               255.255.255.0   U     0      0        0 wlan0


I don't want to have to run this command every time I connect to a network. How can I make it work automatically like it was before?

EDIT: Solved it! The problem also occurred on a live CD for Xubuntu 13.10 which means my router is to blame and not Xubuntu. I fixed it by resetting my router to factory settings and making the changes I needed again.

---

