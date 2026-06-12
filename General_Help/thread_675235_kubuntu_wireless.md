---
title: "kubuntu wireless"
date: 2008-01-22
forum: General Help
---

### Post by zivxx on 2008-01-22
hey everyone, i just bought new laptop and i installed kubuntu on it..and im trying to configure my wireless, but i just got no idea how to do it...
i dunno whats my wireless card tho..does anyone know how to configure the wireless anyway?

---

### Post by user1397 on 2008-01-22
> **zivxx said:**
> hey everyone, i just bought new laptop and i installed kubuntu on it..and im trying to configure my wireless, but i just got no idea how to do it...
i dunno whats my wireless card tho..does anyone know how to configure the wireless anyway?first we need some info on your internet connection:

go to a terminal (Kmenu > system > konsole )  and type: ```
ifconfig
```

then post here what that command returns.

---

### Post by zivxx on 2008-01-22
eth0      Link encap:Ethernet  HWaddr 00:11:43:CC:AA:6E
          inet addr:192.168.123.143  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fecc:aa6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:223381 (218.1 KB)  TX bytes:28435 (27.7 KB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



there you go

---

### Post by user1397 on 2008-01-22
> **zivxx said:**
> eth0      Link encap:Ethernet  HWaddr 00:11:43:CC:AA:6E
          inet addr:192.168.123.143  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fecc:aa6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:223381 (218.1 KB)  TX bytes:28435 (27.7 KB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



there you gohmm, do you see the little network manager icon on the taskbar at the top right of your screen?  what does it look like? have you already tried to configure it through that applet?

---

### Post by zivxx on 2008-01-23
uhhh, my taskbar is in the bottom, and the network manager looks like end of some cable?an end of ethernet cable.
and i tried to configure but everytime i click enable it enable it for a second then auto disable it.
do i need to know some information such as my internet username and passowrd or something called ESSID?

---

### Post by zivxx on 2008-01-23
ok i explored around the network settings once again and i noticed i need to know those:
ESSID
Wep key
and key type
but i really dont know what are those, if anyone can explain to me maybe i could figure them out but i don't know whats the meaning of those.

---

### Post by zivxx on 2008-01-24
hey everyone...i downloaded some more wireless programs from the adept manager but still nothing seems to work :/ i have to give back my cable to my friend soon so if anyone could help me soon as possible that would be great..

---

### Post by zivxx on 2008-01-25
hey everyone..i think im missing some drivers to configure my wireless card..
i have a DELL laptop intel pentium m and well i have this blue"Fn" button that to active wireless(if i had windows) i should click Fn+F2 (on F2 there is like a wireless draw in the same colour of the Fn colour) so what i think that linux doesn't read that when i click Fn+F2...so what i did was runing few tests about this Fn button...i connected my other computer's keyboard and by clicking Fn+F4 it should active the number lock...and i tried and it did activated it...then i got lost...anyone have any ideas?

---

### Post by user1397 on 2008-01-27
try installing ndiswrapper, there are many guides on how to use that...its a wireless internet configuration utility.

---

