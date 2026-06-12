---
title: "My SSD disk is too fast...ethernet is not."
date: 2021-01-22
forum: General Help
---

### Post by kreon28 on 2021-01-22
Yes, seems to be a little bit odd, but my ubuntu session runs very fast and my ethernet connection is not.
The result is that my saved session is opening very fast, so Firefox tabs are with an info : "no connection found" and black screen.
Also my widgets, like weather are returning an error : "No connection".
Ethernet needs about 4-5 seconds more to establish connection.
In the end, I have to refresh all my firefox tabs and the widgets, which is quite abnormal.

Is there any solution to that problem?
(I'm running Ubuntu Studio - 20.10 - with KDE)

---

### Post by TheFu on 2021-01-22
Solution?  Get faster ethernet. Don't use wifi. If you'd like specific help with networking, please provide some details about the hardware setup, WAN connection, router, and drivers.

Firefox has a "reload all" in the right-click menu, so you don't have to click on each tab.

---

### Post by HermanAB on 2021-01-22
Probably a lame DNS. Check your DNS with *dig*.  If bad, use another one.

---

### Post by ActionParsnip on 2021-01-22
Are the client and server systems on the same LAN?

---

### Post by kreon28 on 2021-01-23
Thank you for your answers!

My ethernet cable is connected to router: MikroTik  hAP ac2. Router is connected by cable with modem.
DNS is configured within the router.
Speed of the internet is 600Mb/s.
No other devices is connected to router.
Connection in my ubuntu system is by ethernet cable and it is stable. The only thing is that it is established during startup 4 seconds later than my Plasma has being loaded. 
On my Windows system, I have never noticed such problem. Connection with internet is established immediately.
I wrote that my SSD is to fast, on purpose.
Before moving my same ubuntu system to SSD 2 days ago, I had it on typical HDD earlier. I did not notice such situation, because ethernet may also needed some time to to established, but my Plasma loaded for a bit of time so duration of establishing connection was not noticeable.  

```

[FONT=monospace][COLOR=#000000]dig [/COLOR]

; <<>> DiG 9.16.6-Ubuntu <<>> 
;; global options: +cmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62794 
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 1 

;; OPT PSEUDOSECTION: 
; EDNS: version: 0, flags:; udp: 65494 
;; QUESTION SECTION: 
;.                              IN      NS 

;; ANSWER SECTION: 
.                       512050  IN      NS      a.root-servers.net. 
.                       512050  IN      NS      c.root-servers.net. 
.                       512050  IN      NS      l.root-servers.net. 
.                       512050  IN      NS      d.root-servers.net. 
.                       512050  IN      NS      g.root-servers.net. 
.                       512050  IN      NS      m.root-servers.net. 
.                       512050  IN      NS      j.root-servers.net. 
.                       512050  IN      NS      k.root-servers.net. 
.                       512050  IN      NS      i.root-servers.net. 
.                       512050  IN      NS      e.root-servers.net. 
.                       512050  IN      NS      h.root-servers.net. 
.                       512050  IN      NS      f.root-servers.net. 
.                       512050  IN      NS      b.root-servers.net. 

;; Query time: 19 msec 
;; SERVER: 127.0.0.53#53(127.0.0.53) 
;; MSG SIZE  rcvd: 239
[/FONT]
```

```

[FONT=monospace][COLOR=#000000]lspci [/COLOR]
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controlle
r (rev 06) 
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor
 PCI Express x16 Controller (rev 06) 
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI C
ontroller 
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family 
ME Interface #1 
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI C
ontroller #2 
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Con
troller 
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Ro
ot Port 1 (rev d0) 
00:1c.5 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Ro
ot Port 6 (rev d0) 
00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d0) 
00:1c.7 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Ro
ot Port 8 (rev d0) 
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI C
ontroller #1 
00:1f.0 ISA bridge: Intel Corporation H97 Chipset LPC Controller 
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Cont
roller [AHCI Mode] 
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller 
01:00.0 VGA compatible controller: NVIDIA Corporation GP107 [GeForce GTX 105
0 Ti] (rev a1) 
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Contr
oller (rev a1) 
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/84
11 PCI Express Gigabit Ethernet Controller (rev 0c) 
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge 
(rev 03) 
05:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] 
PCI Multi-Channel I/O Controller (rev 02) 
05:01.0 Multimedia audio controller: Creative Labs EMU20k1 [Sound Blaster X-
Fi Series] 
06:00.0 Network controller: Broadcom Inc. and subsidiaries Device 43c3 (rev 
04)
[/FONT]
```

```

[FONT=monospace][COLOR=#000000]lshw -C network [/COLOR]
WARNING: you should run this program as super-user. 
  *-network                  
       description: Ethernet interface 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: enp3s0 
       version: 0c 
       serial: d8:cb:8a:7c:6f:51 
       size: 1Gbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-
fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverve
rsion=5.8.0-40-lowlatency duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=
10.10.0.254 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s 
       resources: irq:17 ioport:d000(size=256) memory:f7200000-f7200fff memo
ry:e2800000-e2803fff 
  *-network DISABLED 
       description: Wireless interface 
       product: Broadcom Inc. and subsidiaries 
       vendor: Broadcom Inc. and subsidiaries 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: wlp6s0 
       version: 04 
       serial: 34:97:f6:b6:c7:e4 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=brcmfmac driverversion=10.28.2 fi
rmware=01-d2cbb8fd latency=0 multicast=yes wireless=IEEE 802.11 
       resources: irq:35 memory:f7000000-f7007fff memory:f6800000-f6ffffff m
emory:e2400000-e27fffff 
WARNING: output may be incomplete or inaccurate, you should run this program
 as super-user.
[/FONT]

```

---

### Post by TheFu on 2021-01-23
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
vendor: Realtek Semiconductor Co., Ltd. 
logical name: enp3s0 
version: 0c 

I have one of those NICs.  It has always been a problem.  I stopped using it and put a $10 GigE NIC from Marvell into the system. I'd planned to get a $25 Intel PRO/1000 NIC later, but haven't gotten around to that.  The Marvell is really old and only gets:
```
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   648 MBytes   544 Mbits/sec    0             sender
[  4]   0.00-10.00  sec   645 MBytes   541 Mbits/sec                  receiver
```
according to iperf3.  The RTL8111 was showing errors and dropping packets, so unacceptable.  Can't tell from the commands whether yours has the packet-drop issue or not.  I can say that there are lots and lots of people posting in these forums with that same NIC (check the version too, that is VERY IMPORTANT), with issues.  Some do eventually find a magic incantation of manually built and installed driver that seems to fix the issue. Every new kernel, they get to rebuild and reinstall their custom driver.  _If it was me, I'd get a PRO/1000 NIC from Intel, disable the Realtek and never worry about this again._

As proof, here's my problem NIC (disconnected):
```
                description: Ethernet interface
                product: **RTL8111/8168/8411 PCI Express Gigabit Ethernet Control**ler
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: **0c**
                serial: NA
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=**r8169** driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:26 ioport:e000(size=256) memory:f7e00000-f7e00fff memory:f0000000-f0003fff

```And the cheapo Marvell that only gets about 500 Mbps:
```
              *-network
                   description: Ethernet interface
                   product: 88E8001 Gigabit Ethernet Controller
                   vendor: Marvell Technology Group Ltd.
                   physical id: 1
                   bus info: pci@0000:04:01.0
                   logical name: eth1
                   version: 12
                   serial: NA
                   size: 1Gbit/sskge
                   capacity: 1Gbit/s
                   width: 32 bits
                   clock: 66MHz
                   capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                   configuration: autonegotiation=on broadcast=yes driver=**skge** driverversion=1.14 duplex=full latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=1Gbit/s
                   resources: irq:16 memory:f7d00000-f7d03fff ioport:d000(size=256)
``` that works.

Just for completeness, 
```
$ lsb_release -d
Description:    Ubuntu 18.04.5 LTS

$ uname -r
5.4.0-62-generic
```

Since I moved to 18.04.5 and the 5.4.x kernel, I have not tried the Realtek NIC. For me, life is too short to deal with bad hardware. The last 5 yrs or so, I've avoided Realtek in my new system builds and have generally been happier. Things "just work".  That isn't to say that Intel stuff is perfect. The 2.5Gbps newer NICs have terrible support on Linux, so I'd say to avoid those as well on any new Motherboards unless you have another NIC that can be used for some months as Intel fixes their 2.5 Gbps Linux support. With really new kernels, it is supposed to be better, to perhaps 21.04 release will make it a non-issue?

---

### Post by kreon28 on 2021-02-03
> **TheFu said:**
>   _If it was me, I'd get a PRO/1000 NIC from Intel, disable the Realtek and never worry about this again._



Could you post a link with a card you are recommending?

---

### Post by TheFu on 2021-02-03
> **kreon28 said:**
> Could you post a link with a card you are recommending?

I'm not in the market and haven't looked at buying a separate NIC in years.  You want one that supports the e1000 or e1000e drivers.  The i210 and i211 NICs from intel aren't too bad either. Those use the igb driver.  I have both on my network, but the i21x NICs are on motherboards. Don't know if they make those for add-on cards.

```
03:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
        Subsystem: ASUSTeK Computer Inc. I211 Gigabit Network Connection
        Kernel driver in use: igb
        Kernel modules: igb

```

Here's one in a desktop:
```
06:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
        Subsystem: Intel Corporation Gigabit CT Desktop Adapter
        Kernel driver in use: e1000e
        Kernel modules: e1000e

```

These have to bonus of being well-supported by BSD systems too. When picking hardware, a quick check of BSD support is a good way to filter the less-than-great hardware for Linux.

---

