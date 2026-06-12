---
title: "fakeap not making AP?!?!?"
date: 2008-04-01
forum: General Help
---

### Post by nvysel24 on 2008-04-01
ok i got fakeap.pl to finally work now its not outputing fake aps it looks like its working but idk 
what im wanting is for u guys to look at the code below and tell me if anything is rong. i had my friend look for the aps that i was making and he couldnt find any of them

david@david-laptop:~$ sudo perl fakeap.pl --interface wlan0 
[sudo] password for david:
fakeap 0.3.1 - Wardrivring countermeasures
Copyright (c) 2002 Black Alchemy Enterprises. All rights reserved

Using interface wlan0:
Using 4 words for ESSID generation
Using 2 vendors for MAC generation
-------------------------------------------------------------------------
/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig0: ESSID=airport         chan=01 
Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig1: ESSID=Access Point    chan=06
 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig2: ESSID=host            chan=09 
Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig3: ESSID=airport         chan=09 
Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig4: ESSID=tsunami         chan=09 
Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig5: ESSID=Access Point    chan=11
 Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig6: ESSID=airport         chan=05 
Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig7: ESSID=tsunami         chan=07 
Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig8: ESSID=tsunami         chan=06 
Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig9: ESSID=tsunami         chan=10 
Pwr=D/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig10: ESSID=host            chan=11 
Pwr=/sbin/iwconfig/sbin/iwconfig/sbin/ifconfig11: ESSID=Access Point    chan=11

---

### Post by nvysel24 on 2008-04-02
awesome thanks guys no help in 10 hrs

---

### Post by shortylonglegs on 2008-06-24
Do you have the HostAP driver [link: [http://hostap.epitest.fi/]("http://hostap.epitest.fi/")] installed?

---

