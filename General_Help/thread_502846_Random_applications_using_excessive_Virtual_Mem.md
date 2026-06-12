---
title: "Random applications using excessive Virtual Mem"
date: 2007-07-17
forum: General Help
---

### Post by gargoyl3 on 2007-07-17
I have recently ungraded from Edgy to Feisty. Previous system has been working for over 6 months with no unexplained problems. Original system was running Myth over this time.

I decided to reinstall from scratch using the live CD and have experienced slowdowns ever since. This is caused by random applications using excessive virtual memory. 
As soon as I hear the disk trashing and get extremely slow mouse response (mouse jumps inches at a time) I find an app using ~1.4gbytes i.e. my total vm size.

So far in system-monitor / top I have seen update manager, synaptic, firefox and java (when running eclipse) and various other apps, including gnome-system-log (when I was looking to see what was causing the problem). Typicall if I kill these apps system carries on working until the next lockup (normally within a couple of hours)

I tried changing video card from old mx440 to a 5700LE from another PC, so I could try the nvidia-glx-new (was using legacy) but still the same problem.

Have tried working by process of elimination and reinstalling and trying barebones system.
Most recent effort was a clean install from live CD, reboot and decided to just install live updates, and update-manager started using excessive cpu while trying scan current apps.

So far the only remaining common component is X, and I don't know where to go from here.

Output from lspci.

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
00:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)

---

### Post by gargoyl3 on 2007-07-22
No responses ??

Doesn't suprise me as I can't make any sense of it either.

Have changes to kubuntu and so far no problems after 3 days.
previous 3 hours was the best I could get.

---

