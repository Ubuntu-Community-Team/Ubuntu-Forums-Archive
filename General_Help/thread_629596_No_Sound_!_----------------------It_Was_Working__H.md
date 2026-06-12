---
title: "No Sound ! ----------------------It Was Working  Help . Ubuntu Gutsy 7.10"
date: 2007-12-02
forum: General Help
---

### Post by bhencetotozo on 2007-12-02
My sound has been working.. All of a sudden it stopped working... I click on the volume control and it says :

**** No volume control GStreamer plugins and/or devices found


I try Preferences>Sounds > , I click on test sound, it says similar error for all drivers (alsa Oss)

****audiotestsrc wave=sine freq=512 !
*** audioconvert ! audioresample !
*** gconfaudiosink: Could not open resource for
*** writing.


I type:  lspci      I get results below.

thiago@Linux_BR-Ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:01.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
03:00.0 3D controller: nVidia Corporation G71 [GeForce 7950 GX2] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GX2] (rev a1)
05:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
05:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)


I think i started getting this problem becausde i realized my Microphone NEVER WORKED. 
So by trying to fix it i downloaded a file called alc888 and typed ./install and after that it stoped working...

so, i wish i never tryed to fix my microphone driver cuz i miss the sound. :(
please help me !

Please help

---

### Post by bhencetotozo on 2007-12-02
I am working on it but so far no results

---

### Post by CheshireMac on 2007-12-04
I'm having the exact same problem. Rhythmbox seems to be the only issue. Internet sound works fine. I was listening to music an hour ago, with no system changes since. 
Earlier today, I did tweak my system for speed. I didn't think that should effect anything though. Some help would be fantastic. I don't know what happened.

---

### Post by wootah on 2007-12-24
Hi there:

I have the exact same issues following an upgrade to Gutsy. Symptoms are completely similar to bhencetotozo with the same error messages with the only difference being that sound was working fine in 7.04.

Any ideas ?

Thanks!

---

