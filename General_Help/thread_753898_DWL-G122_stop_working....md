---
title: "DWL-G122 stop working..."
date: 2008-04-13
forum: General Help
---

### Post by Mia_tech on 2008-04-13
my wireless connection was working just fine and after doing some updates, and restarting my machine, my wlan0 is not showing any where...not in ifconfig, iwconfig or network manager.... any help appreciated.

thanks

---

### Post by ryanhaigh on 2008-04-14
Perhaps posting the output of ```
lspci
``` or ```
lsusb
``` if its a usb device would yeild some helpful information.

---

### Post by Mia_tech on 2008-04-14
here you go.. lspci
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

```

lsusb
```
jorge@ubuntu-box:~$ sudo lsusb
Bus 005 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```

thanks

---

### Post by ryanhaigh on 2008-04-14
Well as you can see the device shows up in the output of lsusb. You say it doesn't appear in the output of ifconfig but what about ```
ifconfig -a
``` which shows all interfaces configured or not. 

What happens when you remove the device and plug it back in. When you plug in the device wait a few seconds and post the last few lines (or the ones that appear relevant) of the command ```
dmesg
```.

Do you know what driver you were using before? I believe ralink chipsets are supported but cant be positive, the output of dmesg should help with that though.

Finally I suspect that this problem has arisen because you have upgraded the kernel (which is the right thing to do but can sometimes cause breakage), you could try using the older kernel by selecting it from the grub menu.

---

