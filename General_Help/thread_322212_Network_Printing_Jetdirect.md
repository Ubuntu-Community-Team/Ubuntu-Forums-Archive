---
title: "Network Printing Jetdirect"
date: 2006-12-20
forum: General Help
---

### Post by RobPotts on 2006-12-20
Hi,

I'm a beginner to Linux and to networking, however I've aquired an old Jetdirect ex plus, and want to network it through my Netgear DG834GT router, so I can print from my desktop duel boot Ubunto/XP (wired), Laptop testing other linux distros (wired) and 2 work laptops running XP (wireless).

I've connected the jetdirect to the router and the router has detected it (orange light on the channel number conntected to).  I press the test page and it all seems to be OK:
TCP/IP Status: Ready
IP Address: 192.0.0.192
Def. Gateway: 192.0.0.192
bootp/dhcp server: 192.168.0.1
I/O card ready
(Loads more info but I should be working not doing this)

As a beginner I am unable to get this working by following the printer set up instructions.  Can someone please tell me if what I want to do is possible & step by step instuctions on how to do it.  I read somewhere I need to change the IP address is this correct?  Do I need to telnet?  what does this involve, I've tried
Telnet 192.0.0.192 and I get the message unable to connect to remote host:netwrok is unreachable.

I'm tring this from a new install of ubuntu 6.10

Any help would be great

Thanks in adavcne
Rob

---

### Post by scrooge_74 on 2006-12-20
Your PC should be able to detect any printer in the lan after a little while or you can tell the printer installer you have a jetdirect and where it is

---

### Post by RobPotts on 2006-12-20
This may be the problem.  before I wired the jet direct up I did have the printer plugged directly into the paralle port, but it wasn't detected, however when I opened windows on the same PC it did detect it and work
Rob

---

### Post by scrooge_74 on 2006-12-20
Does the printer and your PC have are in the same IP range? That could be a problem, probably you have to follow instructions so the printer gets the correct IP range. 

It been a while since I have use one of those, I do remember that after getting the IP address working I can use a browser to configure it, it was a HP 4000N, that I had to configure

---

