---
title: "More of those Dell Computer problems"
date: 2008-07-02
forum: General Help
---

### Post by Lejeune on 2008-07-02
I have an older computer, sorta. Its a Dell Inspiron B130 with Broadcom chipset and the dreaded Dell Mini PCI Wireless network card. The problem I have when I install is that no matter what I try or do I cannot get my wireless card to work. I'm using the windows based installer trying to install Ubuntu 8.04, with the kernel being 2.6, I think. Any help would be appreciated and any more needed information I can provide.

---

### Post by pytheas22 on 2008-07-02
I'm sure we can make it work.  Broadcom chipsets are a pain but things are getting better, and between ndiswrapper, bcm43xx and b43, there's got to be a way to get yours running.

Please install Ubuntu with wubi (you don't have a problem finishing the installation, do you?).  After it's installed, log in and post the output of these commands:
```

lspci
lshw -C Network
```

Please also let me know whether you use a 32-bit or 64-bit kernel, and whether you have access to a wired connection temporarily (so that I can take that into account when providing instructions).

---

### Post by Lejeune on 2008-07-03
Lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) 
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) 
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
lshw -C Network
*-network:0             
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:15:c5:71:d8:e7 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes 
  *-network:1 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:16:cf:0d:2c:df 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 

32 bit and no wired connection, but can use my xp boot to access the web and work from that.

---

### Post by ago on 2008-07-03
It would be better to ask that in the networking forum: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by pytheas22 on 2008-07-03
Thanks for the information.  I think your card should work using the bcm43xx driver (and maybe also b43 but that's not so clear).  Please try this:

1. on a computer that has an Internet connection, download the firmware cutter from [http://ubuntu.secs.oakland.edu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb](http://ubuntu.secs.oakland.edu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb) .  Transfer it to your Ubuntu computer and save it on the desktop there.

2. do the same thing for the file [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) .

3. on Ubuntu, run these commands:

```
cd ~/Desktop
sudo dpkg --install bcm43*
sudo bcm43xx-fwcutter wl_apsta-3.130.20.0.o
```

then reboot and hopefully your wireless will be working.  If it's not, we can try ndiswrapper next, but hopefully that won't be necessary.

---

