---
title: "Install HP laptop alternative drivers."
date: 2016-10-29
forum: General Help
---

### Post by victorluis on 2016-10-29
I want to install alternative controllers Intel and Realtek wireless that came in the UBUNTU operating system factory pre installed. How could you do?

---

### Post by Bucky Ball on 2016-10-29
*Thread moved to **General Help**.*

Welcome. Why? And why are they 'alternative controllers'? Have you looked at what you're using already?

Please give a lot more detail about what you are looking to install, why, and your hardware. You can run these commands quickly for details on the wireless and video (presuming the 'Intel' reference is to Intell video).

```
sudo lshw -C network
sudo lshw -C video
```

If your machine is running fine, why do you need to install alternative drivers? If it is not running fine, better to tell us what the problem is rather than throwing more drivers at it and perhaps compounding the issue. You may well be using the correct drivers already if that is what Ubuntu has installed for you by default. 

If you're having issues, tell us what they are. :)

(There are many drivers already in the Ubuntu kernel. When you install it detects the hardware and installs the best drivers available for it in the kernel generally.)

---

### Post by victorluis on 2016-10-29
These are the drivers that come with the factory installation of UBUNTU 14.04:

[IMG]http://www.vellisimocentersanisidro.host-ed.me/vmannarelli/Captura%20de%20pantalla%20de%202016-10-24%2017_50_04.png[/IMG]

These are the drivers that are installed by default with Ubuntu 16.04 MATE:
[IMG]http://www.vellisimocentersanisidro.host-ed.me/vmannarelli/Screenshot%20at%202016-10-29%2009:17:18.png[/IMG]

What I want is to use the original drivers as seen in the first screenshot.

The wifi works, but sometimes disconnects and reconnects. I think it would be more convenient to have the original drivers. Right now I'm using the installation I did. I copy the command results:

$ sudo lshw -C network
  *-network               
       descripción: Ethernet interface
       producto: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:01:00.0
       nombre lógico: enp1s0
       versión: 07
       serie: 70:5a:0f:d8:e5:10
       tamaño: 10Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       recursos: irq:43 ioport:4000(size=256) memoria:c1200000-c1200fff memoria:c1000000-c1003fff
  *-network
       descripción: Interfaz inalámbrica
       producto: RTL8188EE Wireless Network Adapter
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:02:00.0
       nombre lógico: wlp2s0
       versión: 01
       serie: 68:14:01:42:f6:1b
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=rtl8188ee driverversion=4.4.0-45-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       recursos: irq:49 ioport:3000(size=256) memoria:c1100000-c1103fff

$ sudo lshw -C video
  *-display               
       descripción: VGA compatible controller
       producto: Broadwell-U Integrated Graphics
       fabricante: Intel Corporation
       id físico: 2
       información del bus: pci@0000:00:02.0
       versión: 09
       anchura: 64 bits
       reloj: 33MHz
       capacidades: msi pm vga_controller bus_master cap_list rom
       configuración: driver=i915 latency=0
       recursos: irq:45 memoria:c0000000-c0ffffff memoria:b0000000-bfffffff ioport:5000(size=64)

---

