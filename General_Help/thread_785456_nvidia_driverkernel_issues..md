---
title: "nvidia driver/kernel issues."
date: 2008-05-07
forum: General Help
---

### Post by grazed on 2008-05-07
Ok. So I have been experiencing random lockups with ubuntu for the past year+. Since the release of 7.04. Which in turn has always driven me away from ever taking ubuntu seriously. These lockups are full out system crashes with no logs. They occur every 20-60 minutes after boot, at completely random intervals, even with the computer idle. Basically, diagnosing this through logs is impossible as I have stated the crashes are so severe that it leaves everything completely locked up. Even the lights on my caps lock key and the such.

A few days ago I sat down and really tried to figure things out and document my problem. This can be found here: 

[http://ubuntuforums.org/showthread.php?t=781449](http://ubuntuforums.org/showthread.php?t=781449)

I documented every issue I have had over the past few weeks, including attempts with other distros. Note that the issue with booting a few of them from cd have been solved with an update to my bios, so that is now irrelevant to the situation.

After a TON of research, I came across the nvidia-linux forums, and discovered a bunch of people with similar issues. Some being very similar to mine, some not.

It turns out that the non-free nvidia drivers have conflicts with the current kernel used in most distros at the moment, but only in some hardware. The only way to solve the issue, at least for me right now is to enable the opensource nvidia driver through xorg. This keeps my system rock solid, yet kills all 3d support. Let alone any effects.

I could REALLY REALLY use some help configuring my setup around this. Otherwise using Ubuntu, or most distros for that matter as a primary OS is near impossible with my computer crashing at will whenever it feels saucy.

Thank you.

---

### Post by grazed on 2008-05-08
bump.

---

### Post by grazed on 2008-05-09
anyone? =/

---

### Post by kpkeerthi on 2008-05-09
I look at the other thread you linked. Can't seem to find the graphics card (model) you have? Can you post the output of ```
lspci
```?

---

### Post by danwood76 on 2008-05-09
On what you have read in the nvidia forums is there any specifics about what is causing the crash?

For example could it be an ACPI issue?
You could try disabling ACPI with the Nvidia proprietry drivers loaded to test this out.

---

### Post by grazed on 2008-05-09
> **kpkeerthi said:**
> I look at the other thread you linked. Can't seem to find the graphics card (model) you have? Can you post the output of ```
lspci
```?

It's an integrated chip with 64MB of dedicated memory, and up to 512 of dedicated RAM. It's a Nvidia 6150 go.

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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
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
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

thanks^

---

### Post by grazed on 2008-05-09
> **danwood76 said:**
> On what you have read in the nvidia forums is there any specifics about what is causing the crash?

For example could it be an ACPI issue?
You could try disabling ACPI with the Nvidia proprietry drivers loaded to test this out.

I always thought acpi was there to control fans and power management. =/

will turning it off be hazardous to the notebook?

EDIT: tried this, though it leaves me with a blank screen after boot.

---

### Post by buntunub on 2008-05-09
That looks like an HP laptop lspci... dv2000+  ??

I know on my dv2415, it does lockup randomly when using Compiz with all effects/plugins enabled. Usually when im spinning the cube or playing a 3D intensive game with Compiz on. Currently, I dont think there is any solution to this issue. However, turning Compiz off eliminated the freezing/lockup problem. You will still have 3D with Compiz turned off right? What you need for 3D is - 

[PHP]$glxinfo | grep direct[/PHP]

The output from that should be -

[PHP]direct rendering: Yes[/PHP]

So long as you get that, then your good to go for 3D games and such things.

---

### Post by grazed on 2008-05-09
> **buntunub said:**
> That looks like an HP laptop lspci... dv2000+  ??

I know on my dv2415, it does lockup randomly when using Compiz with all effects/plugins enabled. Usually when im spinning the cube or playing a 3D intensive game with Compiz on. Currently, I dont think there is any solution to this issue. However, turning Compiz off eliminated the freezing/lockup problem. You will still have 3D with Compiz turned off right? What you need for 3D is - 

[PHP]$glxinfo | grep direct[/PHP]

The output from that should be -

[PHP]direct rendering: Yes[/PHP]

So long as you get that, then your good to go for 3D games and such things.

unfortunately it crashes regardless if any effects or plugins are on. It will actually crash at will, under any load whenever it wants, even if completely idle.

It seems to only crash when the nvidia driver is loaded. So my only option at the moment is to use the crappy open source driver which is 2D only, I believe.

---

### Post by shae on 2008-05-09
If you could link me to the information you found, I would appreciate it.  I bet you can find a stable kernel/nvidia driver combo, but you will have to compile the kernel and manually install the nvidia drivers to test it out.  This is of course somewhat time-consuming, but then again you have tried out six distros to try to find a solution so I think you would not mind this possible solution.

After some googling around, I think you should just update to the latest driver from nvidia's site if you are just using the one that comes with Ubuntu.

---

### Post by grazed on 2008-05-10
> **shae said:**
> If you could link me to the information you found, I would appreciate it.  I bet you can find a stable kernel/nvidia driver combo, but you will have to compile the kernel and manually install the nvidia drivers to test it out.  This is of course somewhat time-consuming, but then again you have tried out six distros to try to find a solution so I think you would not mind this possible solution.

After some googling around, I think you should just update to the latest driver from nvidia's site if you are just using the one that comes with Ubuntu.

sounds good, about to give this a shot in a bit. thanks.

---

### Post by foosean010 on 2008-05-11
What model of laptop do you have, because when i run the lspci code, i get the exact same readout that you do:

> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
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
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

I have an HP dv9000 with a p/n of ez458ua.

One thing that I have noticed with mine, is that I cannot use the newest version of video card driver, the 169.* driver.  This causes the TTY's to become all garbled video, and some lockups when comming out a long idle time. You have to use the last 100.* version of the drivers for your card.  I have read that on a couple of forums, most notably on the sabayon linux forum.  When i have that distro installed, and the 100.*.* version of video drivers, everything worked like a dream for me.  Now, i cannot figure out how to get that same driver to install on mine.

So, no, i would not use the *newest* version of the Nvidia drivers.

---

