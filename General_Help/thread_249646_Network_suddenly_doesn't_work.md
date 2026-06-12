---
title: "Network suddenly doesn't work"
date: 2006-09-02
forum: General Help
---

### Post by Roman27 on 2006-09-02
I rebooted today after being up for a long time.  I wish I would have executed an "uptime" command or something to check.  Anyway, I haven't had any problems like this before, but when my PC came up I was unable to access the network.

Here's my setup:

```
cable modem <--> m0n0wall <--> D-Link switch <--> PCs
```

I rebooted several times, but still no network/Internet connectivity.  Then I ran an "ifconfig" and got this:
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:When I came0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
```

What happened to my eth0?!?!  :confused:  I then ran "sudo ifup eth0" and got this:```
ifup: interface eth0 already configured
```

What does it mean "already configured"?  My PC no talky-talky.  Sumptin' ain't cornfiggered!  :(  Then, I ran "ifconfig -a" and got this:
```
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:9D:55:E6
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:When I came0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

It appears that my eth0 is there, but it's not getting an IP??  So, I ran "sudo dhclient" and got this:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

execve (/lib/dhcp3-client/call-dhclient-script, ...): Permission denied
Listening on LPF/eth0/00:0c:f1:9d:55:e6
Sending on   LPF/eth0/00:0c:f1:9d:55:e6
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
execve (/lib/dhcp3-client/call-dhclient-script, ...): Permission denied
```

Strange.  It's always been able to receive an IP before.  I rebooted the m0n0wall, just to make sure that's ok.  Other machines on the network are able to obtain an IP address and this (the broken) machine is able to receive an IP when I boot to my Windows XP Home partition.

I managed to fix the problem by going into System --> Administration --> Networking and setting a static IP address.  How weird though...  Anyone have any idea of what happened?  Could it be the result of a bad update or something?  I would like to switch back to DHCP.  I hope I can.

---

### Post by David Corrales on 2006-09-02
The dhcp client for debian machines is kinda crazy sometimes... I had that happen to me because of a wrong module once (tulip) and other times just because it was having a bad day lol.

---

### Post by Roman27 on 2006-09-06
Does anyone have any other ideas about what's going on?  Am I the only one to experience this issue recently?

---

### Post by marianom on 2006-09-06
did you install any update before this happens?

---

### Post by TDKBacke on 2006-09-06
> **Roman27 said:**
> Am I the only one to experience this issue recently?
No. You will find more victims here: [http://ubuntuforums.org/showthread.php?t=246557](http://ubuntuforums.org/showthread.php?t=246557)

---

