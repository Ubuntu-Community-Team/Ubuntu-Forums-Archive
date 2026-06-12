---
title: "Dispaly problem"
date: 2006-11-23
forum: General Help
---

### Post by jeherul on 2006-11-23
i am using UBUNTU 6.10 64bit . My haradware configuration is

Processor : AMD athlon 64 2800
Motherboard: Asus 

When i  install it it instal fine . but after that there is a problem in display . THE WINDOW DONOT MOVE PROPERLY AND WHEN I SCROLL DOWN MY MOUSE BUTTON 
IT MOVE LIKE A WAVE . Please help me .

---

### Post by taurus on 2006-11-23
Sounds to me like you need to install a driver for your graphic card?  What graphic card do you have in your machine anyway?

---

### Post by jeherul on 2006-11-23
> **taurus said:**
> Sounds to me like you need to install a driver for your graphic card?  What graphic card do you have in your machine anyway?

I am using ASUS motherboard . graphics card is by asus .but i donot know the properly . how i can do that .

---

### Post by taurus on 2006-11-23
Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
lspci
```

---

### Post by jeherul on 2006-11-23
When I type this command ,it shows like bellow



00:00.0 Host bridge: VIA Technologies, Inc. Unknown device 0336
00:00.1 Host bridge: VIA Technologies, Inc. Unknown device 1336
00:00.2 Host bridge: VIA Technologies, Inc. Unknown device 2336
00:00.3 Host bridge: VIA Technologies, Inc. Unknown device 3336
00:00.4 Host bridge: VIA Technologies, Inc. Unknown device 4336
00:00.5 PIC: VIA Technologies, Inc. Unknown device 5336
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. Unknown device 7336
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
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



  I think the it is from via technologies . But when i search for driver in 
via technologies website , there is no driver for UBUNTU linux . Please help me further.

---

