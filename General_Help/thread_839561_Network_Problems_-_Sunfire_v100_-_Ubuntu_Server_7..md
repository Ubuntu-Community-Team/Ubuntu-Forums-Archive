---
title: "Network Problems - Sunfire v100 - Ubuntu Server 7.10"
date: 2008-06-24
forum: General Help
---

### Post by jpelegrin on 2008-06-24
I'm having problems with packet loss for all network connectivity.  Incoming pings are successful 80% of the time, outgoing from the server successful about 75% of the time.  Here is some output data.  Please notice the RX/TX packet errors/drops.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:BA:18:E8:2D  
          inet addr:192.168.1.155  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         [SIZE="3"]RX packets:1082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1113 dropped:0 overruns:0[/SIZE]carrier:1113
          collisions:0 txqueuelen:1000 
          RX bytes:82531 (80.5 KB)  TX bytes:0 (0.0 b)
          Interrupt:9 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
@ubuntu-sun:~$ lspci
00:00.0 Host bridge: Sun Microsystems Computer Corp. Psycho UPA-PCI Bus Module [
pcipsy]
00:03.0 Non-VGA unclassified device: ALi Corporation M7101 Power Management Cont
roller [PMU]
00:05.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compati
ble 10/100 Ethernet (rev 31)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/
V+]
00:0a.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0c.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compati
ble 10/100 Ethernet (rev 31)
00:0d.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
@ubuntu-sun:~$ sudo lshw -C network

Bus error



Any help would be most appreciated.  The server is plugged into a Linksys router, no wireless involved.

Thanks,
Jeremy

---

### Post by jpelegrin on 2008-06-24
As a follow-up, the LED for the second NIC on the server was unplugged, but blinking rapidly.  I plugged this NIC into a hub and activated it and while I am still receiving errors, the network communication is reliable.  I will use both NICs and split the listeners between them.

Thanks,
Jeremy

---

### Post by promodus on 2008-06-29
could you run
```
ethtool -i eth0
```

---

### Post by jpelegrin on 2008-08-08
driver: tulip
version: 1.1.15-NAPI
firmware-version:
bus-info: 0000:00:0c.0

Sorry for the delay.  Networking is working, but I have to restart it every hour or so.  Still lots of errors.

          inet addr:192.168.1.80  Bcast:192.168.1.255  Mask:255.255.255.0                                                                         
          inet6 addr: fe80::203:baff:fe18:e82d/64 Scope:Link                                                            
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                                            
          RX packets:17891 errors:1 dropped:4525 overruns:0 frame:2                                                                   
          TX packets:282665 errors:771 dropped:0 overruns:3 carrier:771                                                                       
          collisions:7814 txqueuelen:1000                                         
          RX bytes:2483898 (2.3 MB)  TX bytes:76714602 (73.1 MB)                                                                
          Interrupt:9                     

eth1      Link encap:Ethernet  HWaddr 00:03:BA:18:E8:2E                         
          inet addr:192.168.1.81  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:baff:fe18:e82e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:277869 errors:0 dropped:4661 overruns:0 frame:0
          TX packets:3020 errors:467 dropped:0 overruns:2 carrier:466
          collisions:79 txqueuelen:1000
          RX bytes:69521057 (66.3 MB)  TX bytes:189682 (185.2 KB)
          Interrupt:10 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:50202 (49.0 KB)  TX bytes:50202 (49.0 KB)

---

