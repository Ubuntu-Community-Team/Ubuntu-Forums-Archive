---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct"
date: 2022-09-06
forum: General Help
---

### Post by jatineviem on 2022-09-06
Hello guys,

I wanted to install AMD GPU drivers, following the official guide, executing "**amdgpu-install**". However at one point it stopped. Computer was stuck/not responsive at all. After about 30-40min of unresponsive computer, I had to power off my laptop.
Now, the computer boots without problems and also works well.
However, If I try to install anything, I receive following error:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the proble
```
If I enter **sudo dpkg --configure -a** it stops always at the same point: **Building initial module for 5.15.0-46-generic.** 

If I enter **amdgpu-install **it stops at the same point.


According to some posts found in askubuntu, I performed following:
```
cd /var/lib/dpkg/updates

sudo rm *
sudo apt update 

sudo apt upgrade
``` 

The last command stops / computer unresponsive at 28%. After3 hours, it is still at 28%. No move within 3 hours, computer hardly responsive (mostly unresponsive).

Can anyone advise please ?

Computer info: GPU Radeon 8750
```
[FONT=monospace][COLOR=#000000]
Linux computer 5.15.0-46-generic #49~20.04.1-Ubuntu SMP Thu Aug 4 19:15:44 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]

[/FONT][FONT=monospace][COLOR=#000000]lspci [/COLOR]
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09) 
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) 
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) 
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) 
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04) 
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04) 
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4) 
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) 
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04) 
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04) 
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) 
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04) 
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] 
02:00.0 Ethernet controller: Qualcomm Atheros QCA8172 Fast Ethernet (rev 10) 
03:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
[/FONT]
```

Thank you.

---

