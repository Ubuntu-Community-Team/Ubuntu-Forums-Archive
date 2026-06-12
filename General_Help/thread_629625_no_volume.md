---
title: "no volume"
date: 2007-12-02
forum: General Help
---

### Post by twist2b on 2007-12-02
sorry but i cant get any volume! everything works 100% except i have an HP and its reconizing the volume and when i touch the buttons it reacts... but the light is always orange for mute or unmute.. (that means its staying on mute no matter what...... so what do i do to make it work? please pelase help :P


oo sorry i posted this in the wrong place before admins.... you can delete the other one in desktop effects

---

### Post by FuturePilot on 2007-12-02
Can you post the output of 
```
lspci
```
And what model HP is it?

---

### Post by twist2b on 2007-12-02
ok,

[PHP]lspci
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
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)
[/PHP]

yea its all working awsome besides the fact that no sound is emmited... and the light is always orange on the keyboard! lol

---

### Post by matthewcraig on 2007-12-02
What is the output of "aplay -l"

---

### Post by twist2b on 2007-12-02
[PHP]aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/PHP]

---

### Post by matthewcraig on 2007-12-02
So far, so good.  Now, in GNOME, open Preferences->Sound and Preferences->Volume Control.

In Volume Control, go to preferences and check all the boxes for all the devices.  Turn them all up to 100% and make sure none are muted.  Next, go to the Sound, and test the devices until you find one that produces a tone.  If you don't get a sound after that, then the problem exists between the soundcard and speakers.

---

### Post by twist2b on 2007-12-02
i dont have sound and preferences... so now what dod i do?

---

### Post by matthewcraig on 2007-12-02
No menu items?  Are you using GNOME?  If so, use System->Preferences->Main Menu to get those menu items back on your display!

---

### Post by twist2b on 2007-12-02
yea for some reason it was not on my display :'( but i got it up thanks to you.... NOW i have tried and it still doesnt work... and the orange lights not blue like it should on my keyboard

---

