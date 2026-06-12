---
title: "No Sound!!! Using Ubuntu Gutsy. Please Help..."
date: 2008-04-05
forum: General Help
---

### Post by david sousa on 2008-04-05
Hello people! I'm new with this kind of system! and i'm using ubuntu gutsy! I I cannot hear any sound from my desktop! The music and the video is playing but i cant hear it. Please help! I have tryed everything, but is dificult for me do work with this!

My lspci:

> 
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


In sound proprieties i have the option auto-detect for everything and the pop-up says: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

Any solutions?

---

### Post by RedPandaFox on 2008-04-05
Have you got a sound card or is it integrated into you motherboard?

---

### Post by david sousa on 2008-04-05
I dont really know! how can i know that?

---

### Post by ibuclaw on 2008-04-05
> [QUOTE]00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
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
05:00.1 Audio device: ATI Technologies Inc Unknown device aa08 [/QUOTE]

Looks like a motherboard Audio Soundcard to me...

Unless you're using a USB Soundcard and don't know it. :lolflag:
What else, other than Auto-Detect can you set the soundcard to in the Sound Preferences?

[EDIT]
Onboard Soundcard. Built-in to your motherboard. Sticks out of your PC Case in the centre of everything.
_________________________________________________________________________
PCI Soundcard. Detachable. Sticks out of you PC Case towards the bottom where the Metal Slots are.
_________________________________________________________________________
USB-Soundcard. External. Connects via USB.

Regards
Iain

---

### Post by david sousa on 2008-04-05
I have this options:

USB, ALSA, ESD, OSS

But they give me all the same error

---

### Post by david sousa on 2008-04-05
And my soundcard is onboard! thanks! Now! What do i'm going to do?

---

### Post by david sousa on 2008-04-05
HEY! anyone help me?

---

### Post by ibuclaw on 2008-04-06
I've just noticed, you've made a [new thread]("http://ubuntuforums.org/showthread.php?p=4660558#post4660558").

I've moved my post there.

Regards
Iain

---

