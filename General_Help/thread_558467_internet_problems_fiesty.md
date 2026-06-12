---
title: "internet problems fiesty"
date: 2007-09-24
forum: General Help
---

### Post by linuxneewbie on 2007-09-24
I used to have Kubuntu running with a router, and when the wireless windows network crapped out i moved my Linux pc into the room that the windows vista pc was in so we could share a wired connection. As soon as I moved it, it wouldn’t work connected with the router, a workgroup switch, and the cable modem. I thought it was the distribution and tried damn small linux, debian, and ubuntu . they all said connected to eth0 and Firefox says server not found, when I try to ping a website it returns unknown host. 

Any advice?

---

### Post by McNils on 2007-09-24
Sounds like a DNS problem (migth even depend on the dhcp server not sending dns info). Do you have a good dns server in /etc/nsswitch.conf? I think that you can add them manually. But I don't remember exacly where you do that... 

To verify that this is a dns problem try to ping a server using its ipadress.
ping 209.85.135.103
(google)

---

### Post by linuxneewbie on 2007-09-24
Thanks.
 I pinged 209.85.135.103 it returned "From 169.254.6.76 icmp seq=1 Destination Host Unreachable" it kept trying.

I entered /etc/nsswitch.conf in firefox and it said
passwd:compat
group:compat
shadow:compat

hosts: files mdns4_minimal  [NOTFOUND=return] dns mdns4
networks: files

protocols: dbfiles
services: dbfiles
ethers: dbfiles 
rpc: dbfiles

netgroup: nis



Will this be an easy fix?

---

### Post by Shazaam on 2007-09-24
How do you have your connection set up in Firefox? Direct or proxy?

---

### Post by linuxneewbie on 2007-09-24
I've tried both.

---

### Post by McNils on 2007-09-26
It looks like you are having a network problem. Do you get an ipadress? Use  ifconfig to find out.

---

### Post by linuxneewbie on 2007-09-27
Is it normal to have two different one in different categories? The subnet mask looks off. It says 225.225.0.0
And the other one says 225.0.0.0 
With it not working with 4 different distributions could it be my hardware?

---

### Post by linuxneewbie on 2007-09-29
I tried connecting with a usb cord and still have the problem.

---

### Post by McNils on 2007-09-30
Can you post the result of ifconfig?

---

### Post by linuxneewbie on 2007-10-08
It was connected to the modem with a usb cord when I did this. 
"eth1       Link encap:Ethernet HWaddr 00:18:co:72:11:86
                UP BROADCAST RUNNING MULTICAST MTU:1500 Meteric:1
                RX packets:2789 errors:0 dropped:0 overruns:0 frame:0
                TX packets:106 erros:0 dropped:0 overruns:0 carrier:0   
                collisions:0 txqueuelen:1000
                RX bytes 133447 (130.3kib)    TX bytes:8728 (8.5 kib)

  eth1:avah   link ecap: etherne tHWaddr 00:18:co:72:11:86
                      inet addr:169.254.5.209 Bcast:169.254.255.255 mask:255.255.0.0  UP BROADCAST RUNNING MULTICASTMTU:1500 Meteric:1


lo             Link Ecap:Local loopback 
               inet addr:127.0.0.1   Mask:255.0.0.0
               Inet6 addr:   ::1/128 Scope host
               UP LOOPBAK RUNNING MTU:16436 Metric:1
                RX packets:976 errors:0 dropped:0 overruns:0 frame:0
                TX packets:976 erros:0 dropped:0 overruns:0 carrier:0 
                collisions:0 txqueuelen:0
                RX bytes:79932(78.0 kib)    TX bytes:(78.0 kib)"

---

