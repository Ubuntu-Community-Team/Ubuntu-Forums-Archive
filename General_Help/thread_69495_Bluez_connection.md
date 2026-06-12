---
title: "Bluez connection"
date: 2005-09-27
forum: General Help
---

### Post by z!cHz@cH on 2005-09-27
I have a problem with bluez connecting to my internet gateway,

these are the steps i follow to make the connection:

1) sudo modprobe bnep
    this step works fine

2) sudo pand --connect 00:03:C9:78:DB:A9
    The first time it asked me for a pin now he doesnt anymore it always
    assumes the pin stays the same. I want it to ask for my pin everytime
    i connect. Is this possible? 9 out of 10 times it doesnt connect at al and
    it doesnt report it on screen. Is there some kind of a logfile for bluez
    conections so i can see why it didnt connect?

3) sudo /sbin/ifconfig bnep0 192.168.4.2 netmask 255.255.255.000
    This works fine if step 2 didnt fail.

4) sudo /sbin/route add default gw 192.168.4.1
    Same here depending on step 2.

If al these steps work i'm able to internet over bluetooth.

---

