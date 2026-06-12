---
title: "No Sound!!! Using Ubuntu Gutsy. Please Help..."
date: 2008-04-05
forum: General Help
---

### Post by david sousa on 2008-04-05
Hello people! I'm new with this kind of system! and i'm using ubuntu gutsy! I cannot hear any sound from my desktop! The music and the video is playing but i cant hear it. Please help! I have tryed everything, but is dificult for me do work with this!

In sound proprieties i have the option auto-detect for everything and the pop-up says: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

My soundcard is onboard!

In the sound properties i have autodetect and the other options are: USB, ALSA, ESD, OSS. But they give me all the same error

My lspci:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
05:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9588
05:00.1 Audio device: ATI Technologies Inc Unknown device aa08

Any solutions?

Thanks for any kind of help

---

### Post by warp99 on 2008-04-05
Well first welcome to ubuntu. Before anything open a terminal and run 'alsamixer' to see if all of you levels are turned up. If that does not help run the following commands:

```
lspci -v |grep Audio
```

and this command:

```
lsmod |grep snd
```

and post the results to this thread.

---

