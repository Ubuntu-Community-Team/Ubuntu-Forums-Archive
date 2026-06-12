---
title: "[SOLVED] Gutsy: Eth0 won't connect at boot"
date: 2007-10-18
forum: General Help
---

### Post by phibit on 2007-10-18
I just upgraded to gutsy on my pc, and it's great. The only problem is everytime I reboot, my PC won't connect to my LAN on boot (like it did with feisty), so I have no internet.

My newby solution is just to unplug/replug my ethernet cable.. That works but i'd like it to just connect on boot. Any ideas?

Thanks

---

### Post by Tlon on 2007-10-18
For whatever reason, Gutsy specified my lan as Eth1 instead of Eth0.  Maybe it did the same with you.  Check your config files.

---

### Post by phibit on 2007-10-18
Thanks! But which configuration files should I check? I don't know where to find 'em.

---

### Post by phibit on 2007-10-21
Is anyone else experiencing this problem? LAN won't connect on boot?

---

### Post by LennyO on 2007-10-21
Hi,
I have the same problem.  Had it with Feisty and now with Gutsy.  I noticed that when Ubuntu boots it always comes back with Network Connected.  But when I display the network connection information, everything is 0.0.0.0 (IP Address, Broadcast Address, Subnet Mask, Default Route Primary DNS, and Secondary DNS).  I have been disabling the connection and then immediately I enable it.  This time when it connects, all of the above information (IP Address, etc.) is correctly filled in.

I haven't been able to determine why it doesn't connect correctly the first time but it always connects correctly the second time.  Hope my workaround saves you from having to remove the cable each time.

---

### Post by fragos on 2007-10-21
To check configuration, left click the Network Manager icon in the applet bar and select "Manual Configuration...".  For DCHP to work correctly my computer must be totaly powered down at the power strip.  Shutdown leaves the system in a standby like state that also provided power to the USB ports.

---

### Post by LanDan on 2007-10-21
> **phibit said:**
> Thanks! But which configuration files should I check? I don't know where to find 'em.

/etc/network/interfaces

---

### Post by phibit on 2007-10-22
here is my /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0. 
#iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

```

I think the problem may be the last bit, with pppoe. In the past, with feisty i used a pppoe connection, but now I'm using LAN. I'll try removing that last bit. Thanks :D

---

### Post by LanDan on 2007-10-22
do you have a router or do you connect directly to your ISP?

if the last one do they gave a static ip or a random one?

---

### Post by phibit on 2007-10-22
YEP! Removing the 
```
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
```
Solved it for me. That was some leftover config from pppoeconf.

Thanks guys.

---

