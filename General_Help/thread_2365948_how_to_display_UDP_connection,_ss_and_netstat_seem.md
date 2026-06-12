---
title: "how to display UDP connection, ss and netstat seems not work"
date: 2017-07-12
forum: General Help
---

### Post by unityforever on 2017-07-12
Adobe Flash RTMFP protocol creats a lots of UDP connection. 
i want to know who are connected to me.

  i can see intense data-send traffic from monitor. 
i can catch the UDP packages flowing via my network card and know their destination.
but i just can't get it from netstat or ss.


  netstat -n only shows some tcp connections. 
ss -u doesn't show useful information either.


  i catched some UDP packages sending to LAN targets. 
those targets even have arp cached on my computer. but i can see no LAN address in netstat or ss.

  needing your help, many thanks to your guys.

---

### Post by Habitual on 2017-07-12
I found
```
netstat -up
```
or
```
ss -up
```
both to work here.

ss -u being the much more brief.

I hope this helps.

---

