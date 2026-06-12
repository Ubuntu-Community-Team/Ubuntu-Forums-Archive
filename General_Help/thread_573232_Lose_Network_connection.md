---
title: "Lose Network connection?"
date: 2007-10-11
forum: General Help
---

### Post by YannL on 2007-10-11
Hi all,

I have Ubunut 7.04 on, with full update and everything works fine. Still few things to sort out but I have a problem with the network. 

After a set time - I haven't been able to determine what trigger this or how long it takes - I lose my network connection. Firefox can't see the internet or my Router and I can't browse my local network.

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1A:92:B2:4D:5E  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:feb2:4d5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48363452 (46.1 MiB)  TX bytes:1694502 (1.6 MiB)
          Interrupt:21 Base address:0xa400 

a) is there a way to "reset" or "reboot" the network driver / system when it crashes?

b) any idea on how to fix this ?

Thanks.

---

### Post by zvacet on 2007-10-11
[https://help.ubuntu.com/community/Router]("https://help.ubuntu.com/community/Router")

---

### Post by YannL on 2007-10-11
sudo /etc/init.d/networking restart sounds good I will try this

I think the problem occur when the computer turn the screen off (power save)

---

