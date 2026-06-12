---
title: "Wifi on xbxo 360 through  computer"
date: 2008-03-20
forum: General Help
---

### Post by SpenceMakesSense on 2008-03-20
MY computer is on a wifi coonnection and thats the only means internet for me. I am not taking internet from my router I am taking internet from a hotspot next to my house. I am wondering if there is a way to take internet from my USB wifi reciever and run internet through the ethernet port on my computer to my xbox 360.

---

### Post by cdenley on 2008-03-20
I think that would work. Just bridge the wired and wireless adapters on your computer. Your /etc/network/interfaces would be something like this
```

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1

```

I think you might need the bridge-utils package
```

sudo apt-get install bridge-utils

```

---

### Post by SpenceMakesSense on 2008-03-20
Well I changed it and got the program. When I hooked it up the xbox live test connection failed when it got to IP

---

### Post by cdenley on 2008-03-21
Did you reboot? Is the bridge working? Did you bridge the correct two adapters?
```

ifconfig -a

```

---

### Post by SpenceMakesSense on 2008-03-23
br0       Link encap:Ethernet  HWaddr 00:1B:B9:7B:0A:75  
          inet6 addr: fe80::21b:b9ff:fe7b:a75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4514 (4.4 KB)  TX bytes:224195 (218.9 KB)

br0:avahi Link encap:Ethernet  HWaddr 00:1B:B9:7B:0A:75  
          inet addr:169.254.5.112  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:1B:B9:7B:0A:75  
          inet6 addr: fe80::21b:b9ff:fe7b:a75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7600 (7.4 KB)  TX bytes:5443 (5.3 KB)
          Interrupt:18 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:B9:7B:0A:75  
          inet addr:169.254.5.112  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86291 (84.2 KB)  TX bytes:86291 (84.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1A:70:A6:55:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:112028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155828680 (148.6 MB)  TX bytes:7062905 (6.7 MB)

---

### Post by SpenceMakesSense on 2008-03-23
maybe I didnt bridge the correct adapters, because when I plug in the ethernet cord it claims I connected to the ethernet cord

---

### Post by cdenley on 2008-03-23
It looks like you would want this in /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
bridge_ports eth0 wlan0

```

---

### Post by SpenceMakesSense on 2008-03-23
Ok ill give that a try
I am tho using Ndiswrapper to use my wifi receiver and I have to reinstall it everytime I reboot

---

### Post by SpenceMakesSense on 2008-03-23
Didn't work, but when I rebooted my wifi came on on its own but I couldnt browse the web at all.

---

### Post by cdenley on 2008-03-23
Doesn't work on your X-box, or neither? Does your computer get assigned an IP? I'm guessing your problem is with the wireless configuration, and I don't know much about wireless.

---

### Post by SpenceMakesSense on 2008-03-23
wel when I changed the network interface thing the internet didnt work on either, I may have to manually enter the IP on the xbox. but Im not sure where to find that information

---

