---
title: "another internet question"
date: 2008-06-30
forum: General Help
---

### Post by jmd9qs on 2008-06-30
hi,

i recently installed hardy on my roomies comp, but for some reason the internet will not work. ive tried messing around with network settings, but nada. any ideas?

---

### Post by Yuki_Nagato on 2008-06-30
Is the router booting up *after* Ubuntu?  There may be a problem if there is no internet connection when you start the computer up.

---

### Post by jmd9qs on 2008-07-01
the router is always on, its for comcast: my phone and tv are hooked up as well

---

### Post by LMP900 on 2008-07-01
I'm assuming this is a wired connection?

---

### Post by jmd9qs on 2008-07-01
yes, it is wired

---

### Post by soccerboy on 2008-07-01
> **jmd9qs said:**
> yes, it is wired

lspci output?

---

### Post by jmd9qs on 2008-07-01
the output is of lspci is this:

---

### Post by jmd9qs on 2008-07-01
> **jmd9qs said:**
> the output is of lspci is this:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

