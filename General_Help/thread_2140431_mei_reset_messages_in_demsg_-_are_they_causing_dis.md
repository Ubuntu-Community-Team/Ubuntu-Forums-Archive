---
title: "mei reset messages in demsg - are they causing disk check every startup?"
date: 2013-04-29
forum: General Help
---

### Post by thomasmilo on 2013-04-29
My new installation:
Xubuntu 13.04 on
Dell Optiplex 755 mini tower
is doing a disk check routine at each startup, for no apparent reason.  Checking demsg I see some messages concerning "mei" (whatever that is).  Could these irregularities be causing the disk checking?
Any way I can further diagnose why my system checks disk on each startup?  So I really have two questions:  Do I have some problem with MEI (and how do I fix it to get rid of these reset messages)?  AND How to stop the disk check at every restart?
Thank you for any insight!  

OUTPUT OF DMESG GREP MEI:
6.518215] mei 0000:00:03.0: setting latency timer to 64
[   16.518249] mei 0000:00:03.0: irq 43 for MSI/MSI-X
[   21.524029] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   27.536019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   33.548023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   39.560023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   45.572020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   51.584028] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   57.596026] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   63.608030] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   69.620022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   75.632018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   81.644030] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   87.656016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   93.668011] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   99.680012] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  105.692013] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  111.704021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  117.716010] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  123.728009] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  129.740015] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  135.752012] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  141.764010] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  147.776010] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  153.788011] mei 0000:00:03.0: unexpected reset: dev_state = RESETING

DETAIL ON THE COMM CONTROLLER THAT SEEMS TO USE MEI:
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0200000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei

THE REST OF THE OUTPUT OF LSPCI:
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)

---

