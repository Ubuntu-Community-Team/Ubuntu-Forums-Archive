---
title: "Can't load few web pages"
date: 2015-03-09
forum: General Help
---

### Post by Nikolay_Andronov on 2015-03-09
Hi,

Got this strange issue since a while. Can't open google, facebook, youtube, gmail and maybe more web pages. No matter which browser I'm using.
I cleared the cache of both firefox and chromium, nothing changed. The interesting part is that is not always like that - sometimes they work like a charm, sometimes they don't. 
On my smartphone everything is working with the same wi-fi as on the laptop. 
I'm running 12.04 LTS if that matters.

---

### Post by TheFu on 2015-03-10
Could be anything - can you narrow down the issue?
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by Nikolay_Andronov on 2015-03-11
```
andronoff@Daemon:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=1.91 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=2.86 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=5.14 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=2.16 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=1.55 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=2.01 ms
^C
--- 192.168.1.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5008ms
rtt min/avg/max/mdev = 1.559/2.609/5.141/1.199 ms
```
```
andronoff@Daemon:~$ ping google.com
PING google.com (216.58.209.14) 56(84) bytes of data.
64 bytes from sof01s12-in-f14.1e100.net (216.58.209.14): icmp_req=1 ttl=57 time=579 ms
64 bytes from sof01s12-in-f14.1e100.net (216.58.209.14): icmp_req=2 ttl=57 time=22.9 ms
64 bytes from sof01s12-in-f14.1e100.net (216.58.209.14): icmp_req=3 ttl=57 time=88.4 ms
64 bytes from sof01s12-in-f14.1e100.net (216.58.209.14): icmp_req=4 ttl=57 time=18.2 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 18.208/177.393/579.928/234.054 ms
```
```
andronoff@Daemon:~$ ping youtube.com
PING youtube.com (173.194.122.8) 56(84) bytes of data.
64 bytes from prg02s12-in-f8.1e100.net (173.194.122.8): icmp_req=1 ttl=57 time=32.5 ms
64 bytes from prg02s12-in-f8.1e100.net (173.194.122.8): icmp_req=2 ttl=57 time=35.6 ms
64 bytes from prg02s12-in-f8.1e100.net (173.194.122.8): icmp_req=3 ttl=57 time=32.0 ms
64 bytes from prg02s12-in-f8.1e100.net (173.194.122.8): icmp_req=4 ttl=57 time=31.9 ms
^C
--- youtube.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 31.908/33.019/35.612/1.520 ms
```
```
andronoff@Daemon:~$ dmesg | grep eth[0-9]
[140512.984027] eth2: no IPv6 routers present
[153865.664207] eth2: no IPv6 routers present
[154652.560020] eth2: no IPv6 routers present
[246797.040028] eth1: no IPv6 routers present
[260838.080250] eth2: no IPv6 routers present
```
```
andronoff@Daemon:~$ sudo lshw -C network
[sudo] password for andronoff: 
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:c6:55:11
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.7-7 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: 0c:60:76:1d:54:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f69fc000-f69fffff
```
```
andronoff@Daemon:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:e8:c6:55:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:f6ae0000-f6b00000 

eth2      Link encap:Ethernet  HWaddr 0c:60:76:1d:54:f1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe1d:54f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13088822 errors:25 dropped:0 overruns:0 frame:32368976
          TX packets:10766071 errors:544070 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:186710129 (186.7 MB)  TX bytes:1277898334 (1.2 GB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35001 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5574620 (5.5 MB)  TX bytes:5574620 (5.5 MB)

```
```
andronoff@Daemon:~$ more /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
```
```
andronoff@Daemon:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth2
192.168.1.0     *               255.255.255.0   U     2      0        0 eth2
```

---

### Post by TheFu on 2015-03-11
Well - the networking parts are all working.

Time to look elsewhere.  Have you ever run those browsers (or any GUI programs) with sudo or gksudo?  I've seen where firefox refused to come up after someone did a **sudo gedit** before. The directory where gnome (or was it gnome2) stores settings was owned by root, so his normal userid could never create any files and all those programs crashed.

Does that make sense?  Everything in your $HOME should be owned by your useid ... except well, it is hard to day - really depends on your use of the system.

---

### Post by Nikolay_Andronov on 2015-03-12
Can't remember running some GUI applications as a root and anyway the machine have been rebooted many times since the problem appeared. 
Strangely, since I posted this thread, everything opens without a problem. I'm just wondering for how long.. 

/home is owned by useid.

---

### Post by TheFu on 2015-03-12
> **Nikolay_Andronov said:**
> Can't remember running some GUI applications as a root and anyway the machine have been rebooted many times since the problem appeared. 
Strangely, since I posted this thread, everything opens without a problem. I'm just wondering for how long.. 

/home is owned by useid.

Rebooting doesn't do anything about wrong permissions.
If it isn't an issue, please mark the thread as **solved** to free resources for other issues.

---

