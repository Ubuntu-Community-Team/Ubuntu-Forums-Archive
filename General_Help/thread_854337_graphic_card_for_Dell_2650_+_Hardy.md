---
title: "graphic card for Dell 2650 + Hardy"
date: 2008-07-09
forum: General Help
---

### Post by sop408 on 2008-07-09
Hi, I have to apologize for my poor English before describing the problem of my laptop.
I have installed Hardy on my laptop=Dell Inspiron 2650.
Then,I wanted to enable visual effects, so I tried to install the driver from EnvyNG by selecting the automatic installation. I think I installed the EnvyNG by the way described in the website of [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
The problem in the screen is that half of the screen goes blank, then other half of the screen shows a white colour. I don't think I did not see any nvidia logo, and the problem happens before the login screen.
Thank you.

---

### Post by overdrank on 2008-07-09
> **sop408 said:**
> Hi, I have to apologize for my poor English before describing the problem of my laptop.
I have installed Hardy on my laptop=Dell Inspiron 2650.
Then,I wanted to enable visual effects, so I tried to install the driver from EnvyNG by selecting the automatic installation. I think I installed the EnvyNG by the way described in the website of [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
The problem in the screen is that half of the screen goes blank, then other half of the screen shows a white colour. I don't think I did not see any nvidia logo, and the problem happens before the login screen.
Thank you.

HI and could you give us some system specs like memory, graphics?
 What resolution are you using and did you try and use the restricted drivers located under system, administration, hardware drivers?

---

### Post by sop408 on 2008-07-09
Hi, overdrank, thank you very much for your suggestions
I have tried to use the restricted drivers, but it caused the same problem.

system specs 
core
       description: Motherboard
       product: Inspiron 2650
       vendor: Dell Computer Corporation
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: PHOENIX TECHNOLOGIES LTD.
          physical id: 4
          version: A13 (03/23/2004)
          size: 101KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect pcmciaboot edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) 4 - M CPU 1.70GHz
          vendor: Intel Corp.
          physical id: 8
          bus info: cpu@0
          version: 15.2.7
          slot: U49
          size: 1700MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts sync_rdtsc cid cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 8KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 512MiB
          capacity: 512MiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: J6A
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: J7A
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV11 [GeForce2 Go]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5

I hope this information is enough.
Thank you in advance.

---

### Post by overdrank on 2008-07-09
description: VGA compatible controller
product: NV11 [GeForce2 Go]
Hi and it appears you are using a Geforce 2 nvidia please post the output of the command in the terminal ```
lspci
``` to confirm. 
I have had no luck with the desktop effects with the geforce 2 models.

---

### Post by sop408 on 2008-07-09
Hi, this is the output of lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller

Thank you

---

### Post by overdrank on 2008-07-09
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
Yea as I feared, Maybe someone else can help but as I stated I have had no luck with the effects on that model of graphics. Good luck and you may try and use the nvidia settings for changing your resolution. Use the alt, F2 keys and enter this command ```
gksu nvidia-settings
```
If they are not installed then search and install via synaptic manager.

---

### Post by sop408 on 2008-07-09
Thank you very much for trying helping me anyway!!
I will try what you told me to do.
I shall google them as well!!!

Thank you very much for your time!!!:)
Best regards
Sop408

---

### Post by bomasro on 2010-02-03
I am having bascally the same problem with my old Inspiron 2650  if I try to install the NVIDIA proprietary 96 driver for this card as recommended when you do a "driver search".   I heard/read setting acpi=off may fix this problem but as of yet have not tried this.   Can anyone confirm that setting acpi=off  will allow usage of this propietary NVIDIA driver available for this nVidia Corporation NV11 [GeForce2 Go] (rev b2) video card ???

---

### Post by sop408 on 2010-02-09
Hi, I do not possess the same laptop anymore, so I cannot confirm you. I am sorry about that.
Good Luck

---

### Post by afrodeity on 2010-02-16
I have Karmic working on a Dell Inpiron 2650. Everthing was working fine. I had compiz enabled. It downloaded the Nvidia drivers, all good. Then the machine's plug was pulled out. I don't have a battery. It started up with half-a-screen the other half black. Restarted and it was okay. Plug got pulled again, and now I'm stuck with half-a-screen. Oops.

---

### Post by afrodeity on 2010-02-16
Solved: to remove the separate instance of x you have to change settings in the bios from simul mode (CRT & LCD) to LCD only. This will remove the separate black screen.

---

