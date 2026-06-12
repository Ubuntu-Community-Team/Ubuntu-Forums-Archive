---
title: "Wireless Network doesn't turn ON!! Can't use WiFi..."
date: 2014-10-28
forum: General Help
---

### Post by bik-npl77 on 2014-10-28
It happened out of nowhere! It was running fine and one time when I restarted the WiFi was not running...I looked over Wireless in Network settings and it was OFF, I tried to ON it but it immediately switched back to OFF. I ran ifconfig and it no longer shows wlan0 as it used to...

```
 eth0      Link encap:Ethernet  HWaddr 78:2b:cb:ed:4e:89  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7a2b:cbff:feed:4e89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6440055 (6.4 MB)  TX bytes:1743114 (1.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:367074 (367.0 KB)  TX bytes:367074 (367.0 KB)


```

---

### Post by grahammechanical on 2014-10-28
For the sake of clarity please open the drop down menu by clicking the network manager icon and confirm

a) that there is an option to Enable WiFi
b) that the Enable WiFi option is ticked
c) that the menu contains a list of WiFi access points in range of the machine.

If you do not have an option to Enable Wifi that that could mean that the wireless adapter in the machine is switched off or not working. The wireless adapter may be disabled in the BIOS or you have an another operating system installed and WiFi was disabled in that OS before the OS was shut down or the machine is a laptop and a key combination is required to power up the wireless adapter.

This is a useful command to run

```
rfkill list
```

It should show something like this

> 0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no




Hard Blocked = something in hardware stopping the wireless hardware from working. Soft Blocked = something in software stopping the wireless adapter from working.

Regards.

---

