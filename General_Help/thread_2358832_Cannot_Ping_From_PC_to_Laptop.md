---
title: "Cannot Ping From PC to Laptop"
date: 2017-04-17
forum: General Help
---

### Post by bencouve on 2017-04-17
Recently I wrote a script on my PC to automatically backup some important files to my wife's laptop. I used ssh to check if the laptop was up and running rsync  to do the backup. A simple script that worked fine for a few days and then suddenly stopped working. 

Now I cannot ping or ssh the laptop but can ping my router from my PC and the laptop. So am a little befuddled as to why this should be. 

I can ping google.com from both machines. I did a little searching for answers on the ubuntu forum for similar posts and found a post that recommended the following. 


doug@test-smy:~$ doug@test-smy:~$ lsmod >mod_before_flush
doug@test-smy:~$ route >route_before_flush
doug@test-smy:~$ sudo iptables -F
[sudo] password for doug:
doug@test-smy:~$ lsmod >mod_after_flush
doug@test-smy:~$ route >route_after_flush
doug@test-smy:~$ diff mod_before_flush mod_after_flush
1a2,4
> iptable_filter         12706  0
> ip_tables              17791  1 iptable_filter
> x_tables               21974  2 ip_tables,iptable_filter
doug@test-smy:~$ diff route_before_flush route_after_flush

My PC generated no results from the diff and the laptop only gave la2,4 on the diff mod before and after. The above data is only 
copied and pasted from the forum post.

So, any advice welcome. Thanks in advance ...

---

### Post by SeijiSensei on 2017-04-17
Does the laptop get its address via DHCP?  Did it get a different IP address?

---

### Post by bencouve on 2017-04-18
Hello SeiniSensei
Thank you for your response. I very much respect your skills ( you have helped me before).

I do not know how the IP addresses are allocated but they appear to not have changed so I am assuming they are static. Please see ifconfig -a below

Laptop
wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:86:9e:96  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe86:9e96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:138916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:182759342 (182.7 MB)  TX bytes:9205381 (9.2 MB)

PCenx98ded016840f Link encap:Ethernet  HWaddr 98:de:d0:16:84:0f  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6f52:1fbc:2177:8569/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19018 errors:0 dropped:913 overruns:0 frame:0
          TX packets:17120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14073600 (14.0 MB)  TX bytes:2619842 (2.6 MB)

From PC
# arp -a 
eliza (192.168.1.12) at <incomplete> on enx98ded016840f
dsldevice.lan (192.168.1.1) at e0:b9:e5:2b:69:c4 [ether] on enx98ded016840f

from Laptop
# arp -a
vdsldevice.lan (192.168.1.1) at e0:b9:e5:2b:69:c4 [ether] on wlan0

I see that my PC is missing from here

# ping 192.168.1.12
PING 192.168.1.12 (192.168.1.12) 56(84) bytes of data.
From 192.168.1.15 icmp_seq=1 Destination Host Unreachable
From 192.168.1.15 icmp_seq=2 Destination Host Unreachable
From 192.168.1.15 icmp_seq=3 Destination Host Unreachable

I do not think any firewall is running on either machine

# sudo ufw status
[sudo] password for ben: 
Status: inactive

-- get the same result for 192.168.1.12

The the only thing I did recently on my PC was deactivated under Security and Privacy/Files & Applications - Record file and application usage - turned it off! should be my preogative that one ....

---

### Post by bencouve on 2017-04-18
Hmmm, I plugged the laptop directly into the router with cat5 and can now connect. Must assume it is wifi problem. Still not sure though ...

---

### Post by SeijiSensei on 2017-04-18
> Laptop
wlan0 Link encap:Ethernet HWaddr 1c:65:9d:86:9e:96
inet addr:192.168.1.12 Bcast:192.168.1.255 Mask:255.255.255.0

PCenx98ded016840f Link encap:Ethernet HWaddr 98:de:d0:16:84:0f
inet addr:192.168.1.15 Bcast:192.168.1.255 Mask:255.255.255.0


Looks like you had both the wifi and Ethernet adapters connected to the same network.  That can cause all sorts of problems with routing.  Choose one interface and disable the other.

---

