---
title: "Machine has been extremely slow without network"
date: 2008-01-28
forum: General Help
---

### Post by sumanta on 2008-01-28
I have got a strange problem. When the network cable is unplugged, the system  is running very slowly. To launch home, terminal, document viewers, etc it is taking much time. But when I plug the internet cable it works fine. My system has been updated, but still the problem is persisting.

Sumanta

---

### Post by Jimmey on 2008-01-28
Try disabling IPv6 in the network manager. 

Let me know how that goes.

---

### Post by qbox on 2008-01-28
can you post ifconfig pls?
And try to put down network interfaces.

---

### Post by sumanta on 2008-01-30
> **Jimmey said:**
> Try disabling IPv6 in the network manager. 

Let me know how that goes.

I tried to disable IPv6 by blacklisting.
>> Add "blacklist IPv6" in the file /etc/modprobe.d/blacklist
but that didn't work.
Do you know any other way to disable IPv6?

---

### Post by sumanta on 2008-01-30
> **qbox said:**
> can you post ifconfig pls?
And try to put down network interfaces.

ath0      Link encap:Ethernet  HWaddr 00:19:7D:D8:30:2A  
          inet6 addr: fe80::219:7dff:fed8:302a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:19:7D:D8:30:2A  
          inet addr:169.254.5.46  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:16:D3:38:61:D5  
          inet addr:192.168.56.247  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe38:61d5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:852113 (832.1 KiB)  TX bytes:115890 (113.1 KiB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:820 (820.0 b)  TX bytes:820 (820.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-D8-30-2A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:85
          TX packets:353 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:905 (905.0 b)  TX bytes:16238 (15.8 KiB)
          Interrupt:22

---

### Post by dcstar on 2008-01-30
> **sumanta said:**
> I tried to disable IPv6 by blacklisting.
>> Add "blacklist IPv6" in the file /etc/modprobe.d/blacklist
but that didn't work.
Do you know any other way to disable IPv6?

Do a forum search and you will find numerous posts detailing exactly how to disable it.

---

### Post by sumanta on 2008-02-13
> **dcstar said:**
> Do a forum search and you will find numerous posts detailing exactly how to disable it.

Dear David,

I have succeeded to off ipv6, but the problem still persists.

---

### Post by mbeierl on 2008-02-13
Another random thought:  Can you post the output of /etc/hosts, and your host name?  Sometimes not having 127.0.0.1 with your hostname can cause everything to attempt to resolve you local machine via dns, causing long delays, etc...

---

### Post by Trail on 2008-02-14
I had the same problem with an *old* PC, but not with any of the other 4 PC i've tried. I'll check the localhost thing if I boot it again.

---

### Post by sumanta on 2008-02-14
> **mbeierl said:**
> Another random thought:  Can you post the output of /etc/hosts, and your host name?  Sometimes not having 127.0.0.1 with your hostname can cause everything to attempt to resolve you local machine via dns, causing long delays, etc...

Your random thought worked with probability one!
Actually in /etc/hosts 127.0.0.1 the host (i.e. machine name was changed for some unknown reason!).
I just fixed it. It is working fine.
Thanks a lot all of you.

---

