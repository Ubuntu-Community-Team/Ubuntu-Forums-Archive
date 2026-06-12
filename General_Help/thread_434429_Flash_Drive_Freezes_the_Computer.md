---
title: "Flash Drive Freezes the Computer"
date: 2007-05-05
forum: General Help
---

### Post by Sef on 2007-05-05
When I put in a flash drive, my computer freezes up, and I have to reboot.  I have to different flash drives and they both do it.   I tried using Knoppix and the same problem occurred.  Any ideas as to what I can do to fix this?

Note: This happens on 3 usb ports.  The last port simply does not work.  They did work before when XP was on the system.

p4,  512 ram, Nvidia Mx 440 8x.  Below is my pci list:

> 00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a4)


Thank you in advance.

---

### Post by phidia on 2007-05-06
you may want to check /var/log/syslog and messages to see if anything about the lockup is there.
are you using a usb keyboard/mouse or ps/2?

---

### Post by Sef on 2007-05-06
Well the latest is that GRUB is booting...just says please wait, but never does anything.   There is a problem with applications, starting to open but not.   Wondering if I should reinstall and see if the problem gets taken care of.

---

