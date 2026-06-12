---
title: "Can't switch between Intel and AMD Radeon GPU"
date: 2022-09-07
forum: General Help
---

### Post by jatineviem on 2022-09-07
Hello guys, 
could you advise me, how to switch between integrated Intel and dedicated AMD Radeon GPU, for gaming purposes,please ?
[FONT=monospace][COLOR=#000000]**DRI_PRIME=1** seems to have no effect.

[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#54ff54]**tomas@computer**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ uname -a [/COLOR] [/FONT][FONT=monospace]Linux computer 5.15.0-46-generic #49~20.04.1-Ubuntu SMP Thu Aug 4 19:15:44 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
[/FONT]
tomas@computer:~$ sudo apt install amdgpu
[sudo] password for tomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  amdgpu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1&#8239;684 B of archives.
After this operation, 9&#8239;216 B of additional disk space will be used.
Get:1 https://repo.radeon.com/amdgpu/22.20/ubuntu focal/main amd64 amdgpu amd64 22.20.50200-1438746~20.04 [1&#8239;684 B]
Fetched 1&#8239;684 B in 1s (1&#8239;575 B/s)      
Selecting previously unselected package amdgpu.
(Reading database ... 370919 files and directories currently installed.)
Preparing to unpack .../amdgpu_22.20.50200-1438746~20.04_amd64.deb ...
Unpacking amdgpu (22.20.50200-1438746~20.04) ...
Setting up amdgpu (22.20.50200-1438746~20.04) ... 
[/COLOR][/FONT] 	Code:
 	[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#54ff54]**tomas@computer**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lspci [/COLOR]
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

[/FONT][/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][COLOR=#54ff54]**tomas@computer**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ DRI_PRIME=1 glxinfo -B | grep "OpenGL vendor string" [/COLOR]
[COLOR=#ff5454]**OpenGL vendor string**[/COLOR][COLOR=#000000]: Mesa/X.org[/COLOR][/FONT][/FONT]
[/COLOR][/FONT] 
[FONT=monospace][COLOR=#000000]



```



When running steam game, the game is slow, not smooth, fan is rotat[/CODE]ing.  It seems, AMD GPU is not used. At least when checking the game settings,  it sees only the Intel graphic.[/COLOR][/FONT]

---

### Post by &amp;KyT$0P# on 2022-09-07
Are you sure they're dynamically switchable like that (as opposed to being selected at boot time)?

If so, in your place I would try compiling [jammy version of switcheroo-control]("https://packages.ubuntu.com/source/jammy/switcheroo-control") from source on 20.04, and if that succeeds, install the compiled deb package and see if using [FONT=Courier New]switcherooctl launch[/FONT] to run the program runs it with the AMD GPU.

---

### Post by jatineviem on 2022-09-07
Could you let me know, how to select the gpu at boot time ? If you tell me, I can try that. I am newbie penguin.

---

### Post by &amp;KyT$0P# on 2022-09-07
The details of how to do that will be hardware specific, so if you post details of the specific hardware you're using, someone who knows your computer model (or similar) might have some idea.

---

### Post by jatineviem on 2022-09-07
Do you mean BIOS settings ?
Btw hw is lenovo g500.

---

