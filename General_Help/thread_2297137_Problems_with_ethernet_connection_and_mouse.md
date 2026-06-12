---
title: "Problems with ethernet connection and mouse"
date: 2015-10-01
forum: General Help
---

### Post by krwow on 2015-10-01
Hi, i just reinstalled ubuntu, because i bought a ssd and the first time i accidentally installed ubuntu 32 bit version.
With the 32 bit everything worked fine. Now with 64 bit version, i can't connect with my network. Tried some of the stuff
i could find on the web, but didn't work for me. There is a wired connection recognized, but it does not connect.

And the second problem is that my mouse or any other mouse does not work, but it worked with the 32 bit version.

My motherboard is a Gigabyte 970A-UD3P with an updated bios (update: F2g)

I know that you might need some other information like ifconfig print, but i don't know how to get it on the other computer without the mouse.

Thank you.

Edit: Sorry i forget to mention that it's about ubuntu 14.04.
and just found out when i plug and unplug the mouse a couple of times it works, but with my laptop (lubuntu 14.04) it works from the fist time i plug it in.
Ok, my mouse and my usb-stick are only recognized when i use the usb 3.0.

ifconfig
eth0      Link encap:Ethernet  HWaddr fc:aa:14:52:67:02  
          inet6 addr: fe80::feaa:14ff:fe52:6702/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:94 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:822 (822.0 B)  TX bytes:792 (792.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

sudo lshw -C network
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: fc:aa:14:52:67:02
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:29 ioport:d000(size=256) memory:fe800000-fe800fff memory:d0000000-d0003fff

.Okay solved it with [http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

---

