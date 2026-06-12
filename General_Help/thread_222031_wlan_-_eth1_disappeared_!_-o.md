---
title: "wlan - eth1 disappeared ! :-o"
date: 2006-07-24
forum: General Help
---

### Post by AnTaReS7364 on 2006-07-24
Hello,

I have a Broadcom BCM4318 too.
I just succeded to make it works with ndiswrapper, my wifi connection worked fine and I was able to surf on the internet through eth1 which was the wifi card (eth0 is ethernet).
I rebooted my PC, and then ... eth1 has disappeared ! ](*,) 

No possibility to bring it up, <ifup eth1> prints :
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.

It seems like if I have no more wifi card ... And in my network control panel I only see eth0, whereas before I saw eth0 and eth1.
It doesn't appears in the iwconfig output anymore (I just see lo and eth0). 
Does anyone have an idea how to wake up my eth1 ? :confused: 

Thanks in advance,
Olivier

---

### Post by philippe_carlo on 2006-07-24
Can you try
```

sudo modprobe ndiswrapper

```

---

### Post by AnTaReS7364 on 2006-07-24
Yes I had already tried this :neutral: 
I see no difference, eth1 is still away from all the listings (iwconfig, ifconfig ...).

---

### Post by whomever21 on 2006-11-04
mine disappeared, too and i get the same error. i resumed trying out different drivers, but i got the same message each time. i'm guessing something needs to be reset before i go on installing drivers, but what?

i've already tried ```
modprobe -r ndiswrapper
```

---

### Post by fragos on 2006-11-05
It won't appear unless there's a WiFi signal detected.  I found wifi-radar helpful in managing WiFi connections.

---

### Post by AnTaReS7364 on 2006-11-06
Fragos, are you sure of that ?
When I had this problem, the distance between my laptop and the wifi router was about just 1 meter ...
I think this is a software problem.

Finally, I use the eth0 (ethernet cable) instead of wifi, because I didn't succeed to make wifi works :-/

---

### Post by javierfh on 2006-11-06
Hi,

i have different card but similar problem, I cant make the wlan work.
In fact everything seem to be right, the driver and modprobe and everythign but still no flashing lights in the card and the wlan works, because if i boot into XP then works perfectly.

I have tried also this iwconfig and ifconfig but when running these seems like nothing works.
 
So just to try to understand (maybe im totally wrong.. ),Is the ndiswrapper something totally different than iwconfig thing? 
I was just thinking that maybe iwconfig is the way to configure it in linux and when using ndiswrapper you are using the windows drivers and windows way...so no matter what the iwconfig says..
Im probably wrong, but well im just trying to get some light here, to understand the problem so please correct me if you know and well, all help is more than welcome.


Thanks in advance,

Javi

---

### Post by fragos on 2006-11-06
> **AnTaReS7364 said:**
> Fragos, are you sure of that ?
When I had this problem, the distance between my laptop and the wifi router was about just 1 meter ...
I think this is a software problem.

Finally, I use the eth0 (ethernet cable) instead of wifi, because I didn't succeed to make wifi works :-/

This was my actual experience.  At one meter from the access point you have a different issue.  If you installed gnome-network-manager and then tried wifi-radar you will loose the ability to connect until you remove a bit that gnome-network-manger placed in gnome startup.  I believe it had a name like nm-gnome.

---

