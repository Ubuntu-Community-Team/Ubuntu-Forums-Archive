---
title: "Network problem under Breezy"
date: 2005-10-24
forum: General Help
---

### Post by beckyh on 2005-10-24
Hello all,

I have a network problem with my Breezy install (dual boot windows xp) 
The wireless network card has been detected automatically, lights are on, signal strength 100%.  All seems fine.  I can ping the router (192.168.1.1) successfully.  So they are talking together.

Problem is I cannot access internet or email, etc. There is no ISP problem as everything works fine in XP dual boot and am using it now. 

My settings are as follows...

ip address 192.168.1.55
gateway 192.168.1.1
netmask 255.255.255.0
in nameservers is 192.168.1.1 (not sure if this is correct, tried leaving blank aswell but to no avail).

The card is a Belkin wireless F5D7010.  

I am a newbie to linux, if you can help, please speak in laymens terms :-)

---

### Post by fabiand on 2005-10-27
hey,

use the menu to open a terminal, now enter
```
ping 195.90.12.211
```
if get something good (likely no errors) then the nameserver might be your single problem (just enter e.g. 194.25.0.62 ).

If you get errors while pinging ... you will have to look at your routes by using 
```
route -n
```

provide this output in your next post if nothing helps ..

- fabiand

---

### Post by mykey on 2005-10-27
[QUOTE=fabiand]hey,

use the menu to open a terminal, now enter
```
ping 195.90.12.211
```
if get something good (likely no errors) then the nameserver might be your single problem (just enter e.g. 194.25.0.62 ).

If you get errors while pinging ... you will have to look at your routes by using 
```
route -n
```

provide this output in your next post if nothing helps ..

- fabiand[/QUOTE]
did you read the guys post at all ? or are the forums broken ?

---

