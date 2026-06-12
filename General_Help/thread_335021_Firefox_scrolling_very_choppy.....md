---
title: "Firefox scrolling very choppy...."
date: 2007-01-09
forum: General Help
---

### Post by orionMX on 2007-01-09
Just installed 6.10 in dual boot environment.  when browsing with firefox, the scroll function, either with mouse wheel or dragging scrollbar. is extremely choppy and slow.  are there network setting or something that i am missing here.  never had this issue with RH, GENTOO, or any other distro ive sampled.  it is very distracting and renders scrolling vertically almost useless.

thanks

---

### Post by Xerix on 2007-01-09
Perhaps you need to install a graphics card driver.

---

### Post by orionMX on 2007-01-09
am still learning this linux stuff...
how tell do i do that....?

thanks

---

### Post by taurus on 2007-01-09
For nVidia or ATI...

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by taurus on 2007-01-09
> **orionMX said:**
> am still learning this linux stuff...
how tell do i do that....?

thanks

Applications -> Accessories -> Terminal
```
lspci
```
Paste the result here if you don't know which graphic card you have.

---

### Post by orionMX on 2007-01-09
The output from lspci as requested:

~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Communication controller: Conexant HSF 56k Data/Fax Modem
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

the card is a GeForce 6100 integrated if that helps

Thanks

---

### Post by taurus on 2007-01-09
Just follow this guide to install nVidia driver for your graphic card then.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by orionMX on 2007-01-09
Taurus and all...
Thank you all so very much.  Just followed Method 2 of:

> **taurus said:**
> For nVidia or ATI...

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

and.... WOW! It works.

I love LINUX.

---

### Post by chillin.aurora on 2007-01-12
hey! im having the SAME problem as orion.  
and i am also very new to this stuff...................... i am really keen on using linux though, so i'd appreciate any help i can get. 

the output i got from lspci is - 

> 00:00.0 Host bridge: VIA Technologies, Inc. Unknown device 0336
00:00.1 Host bridge: VIA Technologies, Inc. Unknown device 1336
00:00.2 Host bridge: VIA Technologies, Inc. Unknown device 2336
00:00.3 Host bridge: VIA Technologies, Inc. Unknown device 3336
00:00.4 Host bridge: VIA Technologies, Inc. Unknown device 4336
00:00.5 PIC: VIA Technologies, Inc. Unknown device 5336
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. Unknown device 7336
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCIE Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller

help!

thanks

---

