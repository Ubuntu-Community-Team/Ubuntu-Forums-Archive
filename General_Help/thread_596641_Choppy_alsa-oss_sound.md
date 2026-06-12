---
title: "Choppy alsa-oss sound"
date: 2007-10-29
forum: General Help
---

### Post by constchar* on 2007-10-29
The ALSA OSS Emulation Layer (alsa-oss) seems to be choppy from time to time and
choppier in some programs then others.

TeamSpeak2 is horribly choppy and UT2k4 (Linux version) starts to chop up ingame
here and there.

At the moment I have ALSA configured to use my onboard audio card, a RealTek AC'97 with
a NVidia chipset, and I'm not using my second sound card, a Creative Audigy, since I had a
microphone problem with it in Windows XP so now I use the onboard one insted.

Anyone got any ideas how to fix?

Thanks!
Jimmy

---

### Post by Crafty Kisses on 2007-10-29
> **constchar* said:**
> The ALSA OSS Emulation Layer (alsa-oss) seems to be choppy from time to time and
choppier in some programs then others.

TeamSpeak2 is horribly choppy and UT2k4 (Linux version) starts to chop up ingame
here and there.

At the moment I have ALSA configured to use my onboard audio card, a RealTek AC'97 with
a NVidia chipset, and I'm not using my second sound card, a Creative Audigy, since I had a
microphone problem with it in Windows XP so now I use the onboard one insted.

Anyone got any ideas how to fix?

Thanks!
Jimmy

Post the following output:
```
lspci
```

---

### Post by constchar* on 2007-10-29
> **Codename said:**
> Post the following output:
```
lspci
```

```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
05:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
05:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
05:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

---

### Post by sblanzio on 2007-11-03
same problem here. this doesn't affects teamspeak only, but even other software like X-Plane. I guess it is related to OSS.

a solution would be greatly appreciated.

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia

PS I already trie d aoss and modprobe snd_pcm_oss without any result

---

### Post by Mr Groch on 2007-11-05
Same problem here... Very crappy sound when using aoss...

00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)

---

### Post by Brakkvatn on 2008-04-02
There is a problem with Ubuntu's /etc/openalrc configuration file

The ubuntu config file says something like:
 (define devices '(alsa))

In Mandriva it says:
 (define devices '(sdl alsa native esd null))

In Mandriva such games work perfectly.

So replacing (alsa) with (sdl) or replacing the entire line with what is in Mandriva would fix the problem.

Alternativly some sources claim you can edit the local ~/.openalrc file in your home directory instead.

It is odd that Ubuntu has a configuration like this that won't work on many computers.
:popcorn:

---

