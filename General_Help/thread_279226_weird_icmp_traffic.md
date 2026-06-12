---
title: "weird icmp traffic"
date: 2006-10-17
forum: General Help
---

### Post by dhelix on 2006-10-17
Hi,

today i discovered some strange icmp traffic.after i did 
tcpdump -i ppp0 icmp
the output is something like this:

22:56:58.814426 IP XXX.xxx.xxx.xxx > cxxxxxxxxxxx.com.au: ICMP xxx.xxx.xxx.xxx udp port 25205 unreachable, length 98
22:57:17.862099 IP Xxx.xxx.xxx.xxx > xxxxxxxxxxxxxx.cable.ntl.com: ICMP xxx.xxx.xxx.xxx udp port 25205 unreachable, length 98
22:57:23.180720 IP xxx.xxx.xxx.xxx > xxxxxxxxx.brutele.be: ICMP xxx.xxx.xxx.xxx udp port 25205 unreachable, length 142
.....
.....
.....

does anyone know what is this and why my pc responds with this,and how to stop it 


10x in adv!

---

