---
title: "wireless connection is recognized as eth2??"
date: 2012-11-02
forum: General Help
---

### Post by mastrajanis on 2012-11-02
hello i wonder why my wireless connection shows as eht2?? not wlan0? 
some info:
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:44:9f:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth2      Link encap:Ethernet  HWaddr 00:26:5e:25:56:9d  
          inet6 addr: fe80::226:5eff:fe25:569d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6547 errors:0 dropped:0 overruns:0 frame:106354
          TX packets:6491 errors:91 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5580035 (5.5 MB)  TX bytes:1619867 (1.6 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110847 (110.8 KB)  TX bytes:110847 (110.8 KB)
-----------------------------
lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
-------------------------------
sudo cat /var/log/syslog | grep etwork | tail -n20
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info> Activation (eth2) Beginning IP6 addrconf.
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info> Activation (eth2) Stage 3 of 5 (IP Configure Start) complete.
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info> (eth2): DHCPv4 state changed nbi -> preinit
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info> (eth2): DHCPv4 state changed preinit -> reboot
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info>   address 192.168.0.3
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info>   prefix 24 (255.255.255.0)
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info>   gateway 192.168.0.1
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info>   nameserver '192.168.0.1'
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov  2 12:07:06 inspiron-1750 NetworkManager[821]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Commit) started...
Nov  2 12:07:07 inspiron-1750 NetworkManager[821]: <info> DNS: starting dnsmasq...
Nov  2 12:07:07 inspiron-1750 NetworkManager[821]: <info> (eth2): writing resolv.conf to /sbin/resolvconf
Nov  2 12:07:07 inspiron-1750 NetworkManager[821]: <info> (eth2): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  2 12:07:07 inspiron-1750 NetworkManager[821]: <info> Policy set 'virginmedia' (eth2) as default for IPv4 routing and DNS.
Nov  2 12:07:07 inspiron-1750 NetworkManager[821]: <info> Activation (eth2) successful, device activated.
Nov  2 12:07:07 inspiron-1750 NetworkManager[821]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Commit) complete.
Nov  2 12:07:26 inspiron-1750 NetworkManager[821]: <info> (eth2): IP6 addrconf timed out or failed.
Nov  2 12:07:26 inspiron-1750 NetworkManager[821]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov  2 12:07:26 inspiron-1750 NetworkManager[821]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov  2 12:07:26 inspiron-1750 NetworkManager[821]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) complete.
--------------------------------

anyone knows? thank you

---

### Post by grahammechanical on 2012-11-02
From the printout of ifconfig, I would say that you do not have a wireless (wlan) connection at all. I do not see any evidence that you are connected by ethernet (eth0 or eth1) either.

You should see

>  UP BROADCAST RUNNING MULTICAST 

but you only have

>  UP BROADCAST MULTICAST 

When a network device in the machine is connected to the router, then you would see RUNNING alongside the other three.

You should try this command

```
nm-tool
```

That should show you information about your devices, wlan, eth0, eth1. If you have a wireless adapter in the machine and if it has an installed driver you should also see a list of wireless access points in range of your machine. That list should include your wireless access point (the router/hub). If you do not see that list, then Ubuntu is not recognising your wireless adapter and a driver is not installed.

Regards.

---

### Post by mastrajanis on 2012-11-02
> **grahammechanical said:**
> From the printout of ifconfig, I would say that you do not have a wireless (wlan) connection at all. I do not see any evidence that you are connected by ethernet (eth0 or eth1) either.

You should see



but you only have



When a network device in the machine is connected to the router, then you would see RUNNING alongside the other three.

You should try this command

```
nm-tool
```That should show you information about your devices, wlan, eth0, eth1. If you have a wireless adapter in the machine and if it has an installed driver you should also see a list of wireless access points in range of your machine. That list should include your wireless access point (the router/hub). If you do not see that list, then Ubuntu is not recognising your wireless adapter and a driver is not installed.

Regards.
------------------------------------------
Thanks for the reply my nm-tools output:
nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:23:AE:44:9F:5C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth2  [virginmedia] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        00:26:5E:25:56:9D

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKY93887:        Infra, 00:1F:33:1B:E8:8F, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA
    virginmedia6369592: Infra, E0:46:9A:0C:15:50, Freq 2422 MHz, Rate 54 Mb/s, Strength 62 WPA2
    O2wireless0A293C:Infra, 00:1D:68:6A:7B:35, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WEP
    *virginmedia:    Infra, E0:46:9A:01:14:DA, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Olgusia i Pawelek: Infra, 74:31:70:B8:0A:F9, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    SKY4AD3D:        Infra, C8:CD:72:94:AD:3E, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
------------------------------
see still show eth0 ???? :-)

---

