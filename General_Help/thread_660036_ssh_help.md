---
title: "ssh help"
date: 2008-01-06
forum: General Help
---

### Post by phimurh on 2008-01-06
I have a F4C box on my network which i access off of my Ubuntu laptop. I have ssh up and it serves my network fine. I forwarded ssh(p22) through my one router and then again from that router through a VoIP router which has a direct connection to the internet. the F4C box has a static local Ip of 192.168.0.3.

ifconfig of F4C box
[root@tinytux ~]# ifconfig
eth0 Link encap:Ethernet HWaddr 00:10:B5:39:94:17
inet addr:192.168.0.3 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::210:b5ff:fe39:9417/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:421787 errors:0 dropped:0 overruns:0 frame:0
TX packets:4989 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:133800096 (127.6 MiB) TX bytes:1760877 (1.6 MiB)
Interrupt:9 Base address:0x2000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:7238 errors:0 dropped:0 overruns:0 frame:0
TX packets:7238 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:354591 (346.2 KiB) TX bytes:354591 (346.2 KiB)


network map of F4C box from ubuntu box on local IP

phi@laptop32:~$ nmap 192.168.0.3

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-06 11:41 EST
Interesting ports on 192.168.0.3:
Not shown: 1694 filtered ports
PORT STATE SERVICE
22/tcp open ssh
25/tcp closed smtp
80/tcp open http

Nmap finished: 1 IP address (1 host up) scanned in 30.407 seconds
phi@laptop32:~$

newtowk map of network from external address

phi@laptop32:~$ nmap XX.XXX.XXX.XX

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-06 11:44 EST
Interesting ports on cpe-XX-XXX-XXX-XX.neo.res.rr.com (XX.XXX.XXX.XX):
Not shown: 1691 closed ports
PORT STATE SERVICE
1/tcp filtered tcpmux
11/tcp filtered systat
22/tcp filtered ssh
79/tcp filtered finger
80/tcp open http
6667/tcp filtered irc

Nmap finished: 1 IP address (1 host up) scanned in 12.783 seconds
phi@laptop32:~$

---

### Post by ingo on 2008-01-06
so what exactly is your problem???

---

### Post by phimurh on 2008-01-06
I cannot access it from outside my network

---

### Post by ingo on 2008-01-06
Cheers phimurh,

so you cannot access your FC4 server box (located at home) from the great wide world but no probs from within your own home network.

Sounds very much like a firewall problem to me. Most routers these days have firewalls built in, some more, some less restrictive, but my guess is that you have to tell each one that port 22 is to be opened.

BTW, if I were you I'd use a different port than the default one, but get it working first :)

---

### Post by bodhi.zazen on 2008-01-06
> **phimurh said:**
> I cannot access it from outside my network

1. You need to firrst configure you router to forward port 22, or whatever you change it tol

2. You then need a public IP. You can look at something like[ DynDNS](https://www.dyndns.com/)

3. Be sure to understand security : [uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by phimurh on 2008-01-06
found it, it was a problem with my route config on my F4C box

---

