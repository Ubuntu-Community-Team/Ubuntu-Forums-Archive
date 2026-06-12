---
title: "Ubuntu 20.04: how to switch from dedicated GPU to internal GPU"
date: 2021-10-07
forum: General Help
---

### Post by bingodingo on 2021-10-07
Hi,
On Ubuntu 20.04: wanting to switch (temporarily) from dedicated GPU to internal  GPU. (Ultimately wanting to set up a GPU passthrough virtual Ubuntu 20.04 on top of a host Ubuntu 20.04.)
Specs:

Desktop: i9 9900k, Gigabyte Z390 Aorus Pro Wifi, RX 6800 XT, G.Skill Trident Z Neo 32GB (2x16GB) 3600MHz.

2 GPUs plus audio from lspci -k:
00:02.0 Display controller: Intel Corporation UHD Graphics 630 (Desktop 9 Series) (rev 02)
    DeviceName: Onboard - Video
    Subsystem: Gigabyte Technology Co., Ltd UHD Graphics 630 (Desktop 9 Series)
    Kernel driver in use: i915
    Kernel modules: i915

00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
    DeviceName: Onboard - Sound
    Subsystem: Gigabyte Technology Co., Ltd Cannon Lake PCH cAVS
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci

03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 73bf (rev c1)
    Subsystem: Tul Corporation / PowerColor Device 2406
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device ab28
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device ab28
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

Thanks in advance.

---

### Post by grahammechanical on 2021-10-08
Surely this is done in the UEFI settings utility. It could be that when the amdgpu driver was installed it also installed a settings to utility to adjust the working of the amdgpu driver.

If this machine came pre-installed with Microsoft Windows then the supplier may have provided a Windows utility that controls the working of this hybrid graphics system. What does the motherboard manual say about all of this?

Regards

---

### Post by bingodingo on 2021-10-08
Hi Graham, thanks. Sounds correct. The manual refers to 'Internal Graphics Enables or disables the onboard graphics function.' My version of the bios (F12) looks quite different to the manual - though it has this item and 'select initial graphics'. However even after setting both these items appropriately it still seems to be the graphics card that's selected for output when Ubuntu boots. Not sure what to make of that.

The hardware seems to be otherwise working fine - with a HDMI connection to the monitor (prior to making the above changes) the iGPU seemed to be working like a secondary display whilst the card was connected to the monitor via DP cable (gives some of the Ubuntu screen, but not e.g. left vertical margin / favourites). After the above changes there doesn't seem to be any output via the iGPU. Again, don't know what to make of this.

The machine is custom built by me, Windows was not pre-installed. Looks like I can control the display output in there from Settings -> System -> Multiple  Displays /or Advanced Display Settings. (I'm not going to play around too much as I don't have a second monitor, I'm a little worried I'll mangle the installation in a wierd state.). 

Pretty confident this is not an issue with either the hardware or bios; I think if I had the iGPU connected to a second display it would probably all run pretty smoothly.

---

