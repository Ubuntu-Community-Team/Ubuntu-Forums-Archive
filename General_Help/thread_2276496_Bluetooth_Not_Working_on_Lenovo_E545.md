---
title: "Bluetooth Not Working on Lenovo E545"
date: 2015-05-02
forum: General Help
---

### Post by Myst1234 on 2015-05-02
Hi everyone,

I've been trying to sort this out for a while now. It appears my new Lenovo E545 SHOULD have bluetooth capability, however, it will not show up in Bluetooth settings.

Anything I should be running, installing, re-installing etc.?

EDIT:
Running Trusty on a Gnome desktop environment

---

### Post by jeremy31 on 2015-05-18
Post the terminal results of ```
lspci -nnk | grep -iA2 net; rfkill list all; lsusb; uname -a; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
```

---

### Post by Myst1234 on 2015-05-18
Output of
```
 lspci -nnk | grep -iA2 net; rfkill list all; lsusb; uname -a; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
```

```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)    Subsystem: Lenovo Device [17aa:5100]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Lenovo Device [17aa:0179]
    Kernel driver in use: rtl8188ee
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
Bus 002 Device 002: ID 04f2:b44d Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Linux Jarvis 3.13.0-52-generic #86-Ubuntu SMP Mon May 4 04:32:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[    3.299103] Bluetooth: Core ver 2.17
[    3.302148] Bluetooth: HCI device and connection manager initialized
[    3.302159] Bluetooth: HCI socket layer initialized
[    3.302162] Bluetooth: L2CAP socket layer initialized
[    3.302172] Bluetooth: SCO socket layer initialized
[    3.332826] Bluetooth: RFCOMM TTY layer initialized
[    3.332839] Bluetooth: RFCOMM socket layer initialized
[    3.332845] Bluetooth: RFCOMM ver 1.11
[    3.337198] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.337202] Bluetooth: BNEP filters: protocol multicast
[    3.337213] Bluetooth: BNEP socket layer initialized
[    0.005476] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.185481] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.203630] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.317923] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.317937] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.318178] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.318192] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.446126] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    3.488754] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[    9.849215] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
bluetooth             391136  11 bnep,btusb,rfcomm

```

---

### Post by jeremy31 on 2015-05-18
I don't see a bluetooth device listed but btusb is loaded for some reason, please post ```
usb-devices
```

This is a bit strange with btusb loaded and no bluetooth in the rfkill results

---

### Post by Myst1234 on 2015-05-18
The device itself SHOULD have bluetooth. Every manual, forum and support I've been through says the Lenovo ThinkPad E545 has BlueTooth.

Could it be the installation of the distro? Maybe it's corrupted somehow someway?

Output:

```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-52-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:12.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-52-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:13.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b44d Rev=00.03
S:  Manufacturer=SunplusIT INC.
S:  Product=Integrated Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-52-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:12.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-52-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:13.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-52-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.13
S:  Manufacturer=Linux 3.13.0-52-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-52-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:10.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.13
S:  Manufacturer=Linux 3.13.0-52-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:10.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub



```

---

### Post by jeremy31 on 2015-05-18
Can you shutdown the laptop and remove the bottom panel to look at the wifi card?  If it does have bluetooth it should have 2 MAC addresses on it and after a quick google search for rtl8188ee and looking on ebay I can't find one of them that has bluetooth on the wifi card.  I also know that quite a few Lenovo laptops are whitelisted and you can only use certain wifi cards in them or they won't boot

---

### Post by Myst1234 on 2015-05-18
I wasn't able to find my small screwdrivers to take off the back plate. I'll have to check on that later.

The specs on it are BlueTooth 4.0 combination with WLAN. 

Everywhere I've looked mentions a broadcom driver for Windows that will enable BlueTooth. I'm guessing I either need to find that for Linux, or doesn't exist yet?

---

### Post by Myst1234 on 2015-05-18
After a LOT of research, this appears to be a bug/issue with a lot of other people. I have not found any kind of patch or solution as of yet. Lots of LaunchPad bugs reported

---

### Post by jeremy31 on 2015-05-19
Check BIOS settings and see if there is an option to enable Bluetooth.  My Lenovo doesn't have the option but yours is newer

---

