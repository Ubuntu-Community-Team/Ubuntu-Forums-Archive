---
title: "Network?"
date: 2008-07-06
forum: General Help
---

### Post by LinuxLuvver on 2008-07-06
I have 1 pc connected to a linksys AG241 wired gateway.  When i do a traceroute to anyway website there are three entries for my gateway after the ip of my computer i.e. 

192.168.1.65. -- computer ip
192.168.1.1.
192.168.1.1.
192.168.1.1.
xxx.xxx.xxx.xxx -- isp network

  Why are there three steps? I used to only see one step in traceroutes. What could have changed that could be causing this?

Sorry if this is too specific a query for general help.

---

### Post by hal8000 on 2008-07-06
I have the same Linksys AG241 ADSL2 gateway as you. Your question prompted me to do a traceroute to the bbc. I used tracepath, (the same as traceroute but includes MTU information)

anc@orac:~$ tracepath bbc.co.uk
 1:  192.168.254.197 (192.168.254.197)                      0.285ms pmtu 1500
 1:  192.168.254.254 (192.168.254.254)                      1.240ms 
 1:  192.168.254.254 (192.168.254.254)                      0.968ms 
 2:  192.168.254.254 (192.168.254.254)                      0.975ms pmtu 1492
 2:  gamiel-dsl1.ls.zen.net.uk (62.3.86.7)                 39.825ms 
 3:  nietzsche-ge-0-0-2-204.ls.zen.net.uk (62.3.86.205)    38.823ms --snip--

As you can see, I'm also seeing the gateway adress of my router 3 times and some high latencies on my ISP at the moment.

I'm not sure why the gateway is displayed 3 times, but if your network is ok then its nothing to worry about too much.
I'm not sure of your network configuration, but I'm using static addressing on the LAN, (setup in the Linksys router).
The Linksys router points to my ISP's DNS servers and my /etc/resolv.conf points to the Linksys router.

I'm multi booting here, so will try the same test on other linux systems and FreeBSD, I am also curious to know whats happening.

---

### Post by LinuxLuvver on 2008-07-06
This is my tracepath

xxxx@xxxx:~$ tracepath bbc.co.uk
 1:  xxxx.local  (192.168.1.65)                            0.098ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.002ms 
 1:  192.168.1.1 (192.168.1.1)                              1.042ms 
 2:  192.168.1.1 (192.168.1.1)                              1.037ms pmtu 1492
 2:  xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)                    76.140ms asymm  3 

What I'd like to know is are these packets bouncing out or in? my setup is just to use dynamic I think.  What exactly is this file you said that points to the gateway ip? Do I enter 192.168.1.1? It would be handy to have a fixed ip address within my network.

I am not that bothered (well maybe...ha ha) but just wondering what is happening.

---

