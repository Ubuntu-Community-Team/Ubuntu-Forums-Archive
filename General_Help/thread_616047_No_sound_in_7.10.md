---
title: "No sound in 7.10"
date: 2007-11-17
forum: General Help
---

### Post by Zach1234 on 2007-11-17
I just installed 7.10 last night and my sound doesn't work at all. I have all of the sound drivers installed my sound card is a audigy se. lsmod shows this:
zach@MOLDRETH:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
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
01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
 
 I can't select my sound card in sound preferences. I can only select my nvidia and the or my on board card. So how do I get the sound to come out of my audigy card and not the other ones that don't work.

---

### Post by Pumalite on 2007-11-17
pOST:
sudo lshw -C sound

---

### Post by Zach1234 on 2007-11-18
This is what came up:

 *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
  *-multimedia
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106

---

### Post by Zach1234 on 2007-11-18
I got it to work thanks for the help.

---

### Post by swaeshampine on 2007-11-18
well congrats, Zach.
I, however, am still running in circles, as I am new to Linux and would like my sound back!

lshw -C sound:
sebastian@sebastian-nte1:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
sebastian@sebastian-nte1:~$

---

### Post by bmwman91 on 2007-12-06
I am suffering from the same problem.  I have the same sound hardware as the person in post #5, and the same symptoms it seems.  Sound worked until I installed all the package updates (running Mint 4.0 which ~Ubuntu 7.1).  It seems like this is some sort of common problem from my searching...somethign updates so that all the drivers are correct & load, but no sound ever comes out (internal speakers or headphone jack).  Very frustrating.....

---

