---
title: "Help with iptables forwarding for NSTX"
date: 2006-12-23
forum: General Help
---

### Post by sendas on 2006-12-23
I'm attempting to follow this tutorial on my Ubuntu box but I found myself not having the iptables config file in the same place.  [http://thomer.com/howtos/nstx.html](http://thomer.com/howtos/nstx.html) NSTX DNS over IP tunnel

I have eth0 that is 192.168.0.1 and tun0 that is 10.0.0.1

Is this tutorial asking me to forward all my tun0 traffic to eth0? or the other way around. Sorry If i'm not very clear.

Can someone please tell me what I'm suppose to do with this step.

```
# /sbin/ifconfig tun0
tun0      Link encap:UNSPEC  HWaddr XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX
          inet addr:10.0.0.1  P-t-P:10.0.0.1  Mask:255.0.0.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Now you need to enable forwarding on this server. I use iptables to implement masquerading. There are many HOWTOs about this (a simple one, for example). On Debian, the configuration file for iptables is in /var/lib/iptables/active. The relevant bit is:

*nat
:PREROUTING ACCEPT [6:1596]
:POSTROUTING ACCEPT [1:76]
:OUTPUT ACCEPT [1:76]

-A POSTROUTING -s 10.0.0.0/8 -j MASQUERADE
COMMIT

Restart iptables:

/etc/init.d/iptables restart

and enable forwarding:

echo 1 > /proc/sys/net/ipv4/ip_forward

```

---

