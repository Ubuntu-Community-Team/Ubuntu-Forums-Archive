---
title: "Ubuntu 13.04 - No Bluetooth Adapter Found"
date: 2013-05-09
forum: General Help
---

### Post by void00 on 2013-05-09
Hi, I'm using a Dell Inspiron 14R(N4010) laptop.
I recently did a wipe of my entire system and installed Ubuntu 13.04.
I had tried the live cd before installing but forgot to check if bluetooth is working.
It was working fine when I tested it in another similar system. 
There is no bluetooth indicator in the panel, and in the bluetooth settings, it says "No Bluetooth Adapters Found"

The output of rfkill list is as follows:


```
me@system:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

and lspci outputs
```
me@system:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)



```

Another problem I am facing is with the Wireless LAN.
I've installed the Broadcom wireless drivers and I can turn wi-fi on and off.
But it is not detecting wireless networks. 
Everything used to work without errors in  12.04.
What should I be doing to fix these problems?

Thanks.


EDIT: WiFi works fine now. But bluetooth is still not on.

---

### Post by 2F4U on 2013-05-10
Is bluetooth maybe turned off in the BIOS?

---

### Post by void00 on 2013-05-12
Thanks for the reply. I checked the BIOS but Bluetooth is enabled.
I can't figure out why bluetooth would work in another laptop with 
same specs but not in mine. 

Thanks.

---

### Post by 4gsl on 2013-06-11
I have a similar problem. My Logitech MX 5500 keyboard and laser mouse work (both using dongle), but Ubuntu 13.04 says I have no bluetooth adapter. I'm unable to connect any other bluetooth device. Extremely frustrating.

---

### Post by supermango on 2013-12-06
I'm having the same issue.

I am on Ubuntu 13.04. 

I have a Dell stuidio XPS 1645. The bluetooth is enabled in the bios. The button to enable it is the same as the WIFI button. WIFI is working, bluetooth is not.

Any recommendations?

---

