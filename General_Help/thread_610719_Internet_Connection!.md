---
title: "Internet Connection!"
date: 2007-11-12
forum: General Help
---

### Post by Attila2452 on 2007-11-12
i updated my ununtu & it told me to restart after, so i restarted & loggedon and now im internet wont work. what do i do.im at school right now and i j8ust dont know what to do because i have ubuntu on my home comp. i was thinking about trying to find another updaye but i might need internet for it. please elp me. 

P.S. i tried giong in to netwprk , but i didn't know what to do so i didn't touch anything.


 - Attila Hajzer

---

### Post by mikewhatever on 2007-11-12
How do you connect at home? Line modem, wireless? Post the output of ifconfig from a terminal.

---

### Post by Attila2452 on 2007-11-12
line modem on my computer, but i have a router for my sister's laptop. but i use line modem on my computer & there is a problem . i am still new with ubuntu & i dont know how to use the terminal.

---

### Post by Attila2452 on 2007-11-12
what else do you have if this wont work. & i also need some suggestions from others.

---

### Post by mikewhatever on 2007-11-12
Is the router connected to both yours and your sister's pcs? That's the way it should be, both pcs connecting through the router.

Go to Applications>Accessories>Terminal, type ifconfig and hit Enter. Post the output here. The output may show your IP address, so you may want to replace it with xxx. Here's what I get for example:
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:43:80:1B  
          inet addr:172.26.173.30  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::216:d4ff:fe43:801b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:739678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:224015291 (213.6 MiB)  TX bytes:577198827 (550.4 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28346 (27.6 KiB)  TX bytes:28346 (27.6 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:89.xxx.xxx.xxx  P-t-P:172.26.255.17  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:396653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:520398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:167105389 (159.3 MiB)  TX bytes:548230118 (522.8 MiB)


---

### Post by Attila2452 on 2007-11-12
hey ok i got it ... i went to system , Administration , network then i had to type in ym IP and other stuff & then change the setting to auto... but i fixed it :) thanks man ....... i have one more problem. my volume is messed up and i have even tried going to colume control but nothing is working!

---

