---
title: "[SOLVED] How do I start sound modules on startup?"
date: 2008-06-07
forum: General Help
---

### Post by Nepherte on 2008-06-07
I have a on board sound card NVidia CK804 coming along with my motherboard (nforce 4 ultra chipset). I compiled the alsa drivers myself following this guide on alsa-project (corresponding to my sound card): [http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

Sound works fine. But I have to manually modprobe the correct modules to make it work:
```
sudo modprobe snd-intel8x0 ; sudo modprobe snd-pcm-oss ; sudo modprobe snd-mixer-oss ; sudo modprobe snd-seq-oss
```

How do I load these modules automatically on startup?

Additional information:
```
bart@Athena:~$ lspci
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
01:08.0 Multimedia audio controller: Creative Labs SB X-Fi
01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
```

```
bart@Athena:~$ aplay -l
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: CK804 [NVidia CK804], apparaat 0: Intel ICH [NVidia CK804]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: CK804 [NVidia CK804], apparaat 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
```
aplay -l of course only works after i manually modprobed the correct modules.

---

### Post by happyhamster on 2008-06-07
Try adding them to the file: /etc/modules

---

### Post by Nepherte on 2008-06-07
Ok, now that was dumb of me ](*,)

I already added the following from the alsa-project page to my modules:```
       # ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-intel8x0
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss
```
but forgot to add the module options. Obviously, adding them solved the problem.

---

