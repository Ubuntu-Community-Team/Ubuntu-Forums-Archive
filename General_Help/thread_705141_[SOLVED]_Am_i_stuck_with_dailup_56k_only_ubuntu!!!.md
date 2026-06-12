---
title: "[SOLVED] Am i stuck with dailup 56k only ubuntu!!!!!"
date: 2008-02-23
forum: General Help
---

### Post by dragonwings on 2008-02-23
im using ubuntu 7.04 which i have been using dailup 56k 

Now i have the use of a lan/office conection (windows based)
with my windows notebook all i do is plug in lan cable and bingo im surfing

With my ubuntu macbook (Runs only ubuntu 7.04 ) i plug it in and i get nothing 

       help  help help !!!

---

### Post by louieb on 2008-02-23
Weird! Wired networking should work out of the box. 

With the notebook plugged in to the network try these two commands.

list your network connections
```
ifconfig
```and see if you can get an IP address via DHCP
```
sudo dhclient
```If it doesn't work see if you can capture the output of the two commands and paste them in your next post.
Good Luck.

---

### Post by Iowan on 2008-02-23
You can also check **/etc/network/interfaces** file to see if eth0 is set up.  An alternative is to use System>Administration>Network to see if "Wired connection" is checked.

---

### Post by dragonwings on 2008-02-23
jas@jas-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:CB:BE:DF:01  
          inet6 addr: fe80::216:cbff:febe:df01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:CB:CD:86:D9  
          inet6 addr: fe80::216:cbff:fecd:86d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2208 (2.1 KiB)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:16:CB:CD:86:D9  
          inet addr:169.254.10.105  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:364 (364.0 b)  TX bytes:364 (364.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CB-BE-DF-01-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:7
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:4439 (4.3 KiB)  TX bytes:3634 (3.5 KiB)
          Interrupt:16 

jas@jas-laptop:~$ 


------------------------------------------------------------------------------------
------------------------------------------------------------------------------------
jas@jas-laptop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:cb:be:df:01
Sending on   LPF/ath0/00:16:cb:be:df:01
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:16:cb:cd:86:d9
Sending on   LPF/eth0/00:16:cb:cd:86:d9
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
jas@jas-laptop:~$

---

### Post by dragonwings on 2008-02-23
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by dragonwings on 2008-02-23
Thanks for all the help guys ,but i have solved the problem ,it was a loose fitting lan socket on my macbook the weird thing is when i plugged it in it still recognised the lan cable .only when i plugged it in today by chance i noticed the sloopyness  in the connection so i put a book under the lan cable to pack it up and bingo im surfing.

---

