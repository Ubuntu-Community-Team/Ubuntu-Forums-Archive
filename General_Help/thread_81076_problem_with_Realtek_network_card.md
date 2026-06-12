---
title: "problem with Realtek network card"
date: 2005-10-23
forum: General Help
---

### Post by alexx on 2005-10-23
Hi alll,
I am runnig Ubuntu 5.10 but have problems with Realtek network card.
On boot time it says that I should use the 8139too driver instead of 8139cp.
I did : 
```
#rmmod 8139cp
#modprobe 8139too
```

But still no luck. Pinging another host gives me "Destination host unreachable"

Here is some more info:

```
alexx@host:/usr/src$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:95:09:4B:0C
          inet addr:192.168.4.113  Bcast:192.168.7.255  Mask:255.255.248.0
          inet6 addr: fe80::240:95ff:fe09:4b0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1091 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00

--------------------------------------------------------------------------
[4295596.184000] NETDEV WATCHDOG: eth0: transmit timed out
[4295596.184000] eth0: Transmit timeout, status 0c 0005 c07f media 18.
[4295596.184000] eth0: Tx queue start entry 4  dirty entry 0.
[4295596.184000] eth0:  Tx descriptor 0 is 9008a03c. (queue head)
[4295596.184000] eth0:  Tx descriptor 1 is 9008a03c.
[4295596.184000] eth0:  Tx descriptor 2 is 9008a03c.
[4295596.184000] eth0:  Tx descriptor 3 is 9008a03c.
[4295596.184000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
--------------------------------------------------------------------------
```

I've seen people asking about the same problem on the forums but no useful answers found.

Please can someone point me to solution ?

---

### Post by LorenzoD on 2005-10-23
What does route tell you?

---

### Post by alexx on 2005-10-23
```
alexx@host:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.248.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by LorenzoD on 2005-10-23
Are you able to ping your gateway (192.168.0.1)?

---

### Post by alexx on 2005-10-25
no. the same answer : Destination Host Unreachable.

---

### Post by flyingbrass on 2005-10-25
An older version of Knoppix didn't load the needed module for my network card.  To get online I loaded the module as you have done, then to make it work used pump.  You might try pump (probably sudo pump) and see what happens.

---

