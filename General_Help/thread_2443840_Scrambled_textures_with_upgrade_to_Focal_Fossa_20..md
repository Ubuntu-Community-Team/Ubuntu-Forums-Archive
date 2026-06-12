---
title: "Scrambled textures with upgrade to Focal Fossa 20.04 LTS"
date: 2020-05-21
forum: General Help
---

### Post by dslamngu on 2020-05-21
Hello,

I recently upgraded to Fossa from Eoan Ermine. This system is based on an Athlon 3000g with Vega 3 graphics, and it's using the integrated graphics.

I have many Steam games installed for which I see scrambled textures. The symptom is suspiciously common between many of my games. Here are some examples.

Horizon Chase: Turbo
[ATTACH=CONFIG]285942[/ATTACH]

Hollow Knight
[ATTACH=CONFIG]285941[/ATTACH]

Wizard of Legend
[ATTACH=CONFIG]285943[/ATTACH]

Ding Dong XL
[ATTACH=CONFIG]285944[/ATTACH]

Super Bit Blaster XL
[ATTACH=CONFIG]285940[/ATTACH]

I've tried switching Kernel versions - 5.6.14, 5.4.0.31.35, 5.4.0.31.36, and 5.4.0. No success.

I've tried upgrading to the oibaf drivers. No success.

It seems like it doesn't matter whether the games are native or Proton.

All of these games worked perfectly on Eoan but broke when I upgraded to Focal. I'd love a hint for how to fix this. Thanks!

```
[SIZE=1][FONT=courier new]glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: AMD RAVEN2 (DRM 3.35.0, 5.4.0-31-generic, LLVM 10.0.0)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 20.2.0-devel (git-fc06b8b 2020-05-20 focal-oibaf-ppa)
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6 (Compatibility Profile) Mesa 20.2.0-devel (git-fc06b8b 2020-05-20 focal-oibaf-ppa)
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 20.2.0-devel (git-fc06b8b 2020-05-20 focal-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:[/FONT][/SIZE]

[SIZE=1][FONT=courier new]lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 PCIe GPP Bridge [6:0]
00:01.6 PCI bridge: Advanced Micro Devices, Inc. [AMD] Zeppelin Switch Upstream (PCIE SW.US)
00:01.7 PCI bridge: Advanced Micro Devices, Inc. [AMD] Zeppelin Switch Upstream (PCIE SW.US)
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus A
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus B
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 7
02:00.0 Network controller: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso (rev cc)
04:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Raven/Raven2/Fenghuang HDMI/DP Audio Controller
04:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
04:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Raven2 USB 3.1
04:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
05:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61)[/FONT][/SIZE]
```

---

### Post by wildmanne39 on 2020-05-21
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by dslamngu on 2020-05-21
Thank you! First post and didn't know.

---

### Post by dslamngu on 2020-05-23
I was looking for some hints, and it looks like one common element between these is that they use the Unity engine. I see this in the Steam logs.

Logging to /home/dslamngu/.config/**unity3d**/Aquiris/HorizonChaseTurbo/Player.log
Logging to /home/dslamngu/.config/**unity3d**/Nickervision Studios/Bing Bong XL/Player.log
Logging to /home/dslamngu/.config/**unity3d**/Team Cherry/Hollow Knight/Player.log

I have some other games that work fine, including various emulators, that don't use Unity.

Maybe Unity doesn't work correctly with Ubuntu 20.04.

Is this a good way to get help? Please let me know what I should be expecting. I upgraded and now my textures don't work.

---

### Post by dslamngu on 2020-05-24
Update: @Yoska on the /r/Steam Discord pointed me to this issue tracker for Unity.

[https://issuetracker.unity3d.com/issues/linux-nvidia-graphical-corruption-in-many-games-possible-regression](https://issuetracker.unity3d.com/issues/linux-nvidia-graphical-corruption-in-many-games-possible-regression)

Although it covers NVIDIA in particular, the workaround is the same.

For each Steam game, in the Launch Options, I added "-force-vulkan". Once I added that, the texture rendering was perfect.

Thank you to Ubuntu Forums for allowing me to host my issue here. The Unity devs must fix their OpenGL code.

---

