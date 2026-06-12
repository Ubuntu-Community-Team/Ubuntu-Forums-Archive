---
title: "ATI Graphic card X1650 set up with 2 displays"
date: 2019-01-10
forum: General Help
---

### Post by frank18 on 2019-01-10
[COLOR=#000000][FONT=verdana]Hi guys i installed an ATI video card X1650 with 2 DVI outputs with 2 monitors and set displays 1 is 19'' the other is 20'' both 16-9 wide screen,i've set  resolution to 1280-1024, the 19'' monitor has the right screen the other not so much it falls short,check screen pic attach. also it's on Xubuntu 18.04 Distro.Is there anything i can do,thanks [/FONT][/COLOR]

---

### Post by him610 on 2019-01-10
Hello frank18,

The ATI Radeon X1650 is a true legacy graphics card; I used to have a Radeon X850. Which driver are you using? 
How about showing, between the code symbols, the results of *inxi -F*

---

### Post by frank18 on 2019-01-11
Thanks  him610 


```
frank@frank-ET1331G:~$ inxi -F
System:    Host: frank-ET1331G Kernel: 4.15.0-43-generic x86_64 bits: 64
           Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: eMachines product: ET1331G serial: N/A
           Mobo: eMachines model: MCP61PM-GM serial: N/A
           BIOS: AMI v: P01-A2 date: 12/10/2009
CPU:       Dual core AMD Athlon II X2 250u (-MCP-) cache: 2048 KB
           clock speeds: max: 1600 MHz 1: 1400 MHz 2: 800 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV535 [Radeon X1650 PRO]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1280x1024@75.02hz, 1280x1024@75.02hz
           OpenGL: renderer: ATI RV530
           version: 2.1 Mesa 19.0.0-devel (git-8847370 2019-01-05 bionic-oibaf-ppa)
Audio:     Card-1 NVIDIA MCP61 High Def. Audio driver: snd_hda_intel
           Card-2 C-Media driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-43-generic
Network:   Card: NVIDIA MCP61 Ethernet driver: forcedeth
           IF: enp0s7 state: up speed: 100 Mbps duplex: full
           mac: 44:87:fc:70:cc:84
Drives:    HDD Total Size: 250.1GB (4.7% used)
           ID-1: /dev/sda model: ST3250318AS size: 250.1GB
Partition: ID-1: / size: 229G used: 11G (6%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 18.4C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 179 Uptime: 27 min Memory: 652.1/3945.2MB
           Client: Shell (bash) inxi: 2.3.56 
frank@frank-ET1331G:~$
```

---

### Post by him610 on 2019-01-11
How about showing between code tags, the results of *xrandr*

---

### Post by frank18 on 2019-01-12
> **him610 said:**
> How about showing between code tags, the results of *xrandr*



[COLOR=#191919][FONT=&amp]Hi my friend i tried to install  [/FONT][/COLOR]*xrandr  it states in terminal;  not a candidate to install *[COLOR=#191919][FONT=&amp].[/FONT][/COLOR]
[COLOR=#191919][FONT=&amp] though i had it working on both displays with resolution 1280-1024 0.0HZ ,which 0.0HZ is weird since only resolutions under that show up on both displays with no other options and none work right even screw the graffics so much so i have to reboot,and the interesting thing is everytime i reboot it goes to a screen; ''see pics'' a log in with name and password witch i put in and it goes nowhere,then the only way i can go to my desktop is if i do Xubuntu GNU grub recovery mode,this Xubuntu 18.04 is giving me headaches with these 2 monitors[/FONT][/COLOR]

---

### Post by frank18 on 2019-01-12
Ok guys i went the hard way which was reinstalling Xubuntu 18.04 and now it is working right set both monitors  1280-1024 75hz and seems both are set right now,keep my fingers crossed.

---

### Post by him610 on 2019-01-12
Glad to hear you have it working. Please use the Thread Tools to mark it ***Solved***

---

### Post by frank18 on 2019-01-13
> **him610 said:**
> Glad to hear you have it working. Please use the Thread Tools to mark it ***Solved***



thanks bro;  most the times i rather do a fresh install of the OPS then loose too much time figuring out what not right ,you go crazy and loose your cool for nothing,and spend endless time to fix stuff,while reintalling OPS is just a few minutes, anyway here my [COLOR=#191919][FONT=&quot]$ inxi -Gxx[/FONT][/COLOR]

[COLOR=#2C3E50][FONT=&quot][INDENT]frank@frank-ET1331G:~$ inxi -Gxx
Graphics: Card: Advanced Micro Devices [AMD/ATI] RV535 [Radeon X1650 PRO]
bus-ID: 02:00.0 chip-ID: 1002:71c1
Display Server: x11 (X.Org 1.19.6 )
drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
Resolution: 1280x1024@75.02hz, 1280x1024@60.02hz
OpenGL: renderer: ATI RV530
version: 2.1 Mesa 18.0.5 Direct Render: Yes
frank@frank-ET1331G:~$ 
[/INDENT][/FONT][/COLOR]
[COLOR=#2C3E50][FONT=&quot]
[/FONT][/COLOR]

---

