---
title: "[SOLVED] system is Hosed!!!"
date: 2008-06-10
forum: General Help
---

### Post by underdog512 on 2008-06-10
I am running Hardy 64-bit

After installing some modules for VirtualBox and doing about 135 updates there was a system restart required. When I did a restart nothing as far as video and sound is working correctly. 

Soundcard is not working at all and I can only get a 800x600 resolution on the screen.  It almost like all the drivers uninstalled themselves. When go to hardware drivers under system > Administration my Nvidia GeForce 6200 is not there.

Here is the output from lspci 

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
01:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
04:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

As you can see the video and sound card are detected, however the drivers do not seem to be installed for them.

Any ideas on how we can fix this?

---

### Post by underdog512 on 2008-06-10
apparently one of the modules added ubuntu-server to the Grub menu.  when booted ubuntu-generic everything works fine.

How do you edit grub so that it automatically boots ubuntu-generic as opposed to ubuntu-server?

---

### Post by hal8000 on 2008-06-10
> **underdog512 said:**
> apparently one of the modules added ubuntu-server to the Grub menu.  when booted ubuntu-generic everything works fine.

How do you edit grub so that it automatically boots ubuntu-generic as opposed to ubuntu-server?


Just make sure the generic kernel is available in /boot and then edit menu.lst so that the menu.lst points to your kernel.

sudo gedit /boot/grub/menu.lst

will edit the file for you. Post the outputs of:

cat /boot/grub/menu.lst


and also:

ls -l /boot

if you still have trouble.

---

