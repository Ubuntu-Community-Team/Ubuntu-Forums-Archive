---
title: "Which Driver Do I Use?"
date: 2007-02-08
forum: General Help
---

### Post by orcalover on 2007-02-08
Is there a way for me to find out what graphics card I am using? I've looked in the device manager, but nothing pops out at me. 

I'm trying to get Beryl up and running, but something seems to be going wrong. I installed the X-org Nvida driver, but I'm not sure rather I should use the ATI version or not. 

I'm using an ASUS (A8N-SLI Deluxe) mother board with an AMD processor. 

If anyone has any suggestions, I'd appreciate it. 

Thanks

---

### Post by houstonbofh on 2007-02-08
Well, since we can't see inside your box, you will have to.  Try looking inside.  Without knowing brand and series, we are only guessing.  You need to come back with Nvidia 7800 or something that detailed.  7800gs vs. 7800 gt makes no difference, however.

---

### Post by jocko on 2007-02-08
What output do you get when you run lspci in a terminal?

---

### Post by orcalover on 2007-02-08
Okay, here's what is shown on the graphics card:

e-GeForce 6200LE 128MB DDR P/N: 128-TC-2N27-SX

Does this indicate anything? Seems that I have Nvida, but should I use the legacy driver or the new one?

Thanks

---

### Post by orcalover on 2007-02-08
> **jocko said:**
> What output do you get when you run lspci in a terminal?

This is the output

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
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0163 (rev a1)
05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

---

### Post by reclusivemonkey on 2007-02-08
> **orcalover said:**
> Okay, here's what is shown on the graphics card:

e-GeForce 6200LE 128MB DDR P/N: 128-TC-2N27-SX

Does this indicate anything? Seems that I have Nvida, but should I use the legacy driver or the new one?


GeForce is NVIDIA. 6200 shouldn't require the legacy drivers I don't think.

---

### Post by houstonbofh on 2007-02-08
> **orcalover said:**
> Okay, here's what is shown on the graphics card:

e-GeForce 6200LE 128MB DDR P/N: 128-TC-2N27-SX

Does this indicate anything? Seems that I have Nvida, but should I use the legacy driver or the new one?
You have an Nvidia 6200 series card.  This is a solid card and well supported. [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)  You use the real driver, not the legacy one.  (The legacy driver will tell you what cards need it. Very old cards.)

You can also try the scripts at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) for a more current driver.  However, it is no longer in apt for updates.

---

