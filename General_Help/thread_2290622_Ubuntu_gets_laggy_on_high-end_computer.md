---
title: "Ubuntu gets laggy on high-end computer"
date: 2015-08-13
forum: General Help
---

### Post by DJDBgr on 2015-08-13
Hello everyone. I'm having a problem with my Ubuntu 14.04 setup (same thing happened when i tried Linux Mint 17 Cinnamon):

Even though i'm using latest Nvidia drivers and the newest updates, Ubuntu starts feeling lagging after opening a few apps. The most obvious example is when moving a window. When i have 1-2 apps open, moving an open window is fluid and with no problems. If i open some more apps, moving a window around becomes laggish. This difference is obvious even after opening just one more app (px opening Firefox or Opera + Spotify).

Any help would be really appreciated since i can't find a solution.

This is my *inxi -Fx* output:

```
System:    Host: djdblinux Kernel: 3.19.0-25-generic x86_64 (64 bit, gcc: 4.8.2) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: ASRock model: Z97 Extreme4 Bios: American Megatrends version: P1.30 date: 05/23/2014
CPU:       Quad core Intel Core i5-4690K CPU (-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 27991.2 
           Clock Speeds: 1: 3902.500 MHz 2: 3899.082 MHz 3: 3862.304 MHz 4: 3901.132 MHz
Graphics:  Card: NVIDIA GK104 [GeForce GTX 770] bus-ID: 01:00.0 
           X.Org: 1.17.1 driver: nvidia Resolution: 1600x900@60.0hz, 1920x1080@60.0hz 
           GLX Renderer: GeForce GTX 770/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 346.82 Direct Rendering: Yes
Audio:     Card-1: NVIDIA GK104 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1 
           Card-2: Texas Instruments PCM2902C Audio CODEC driver: USB Audio usb-ID: 001-007 
           Card-3: Microsoft LifeCam HD-5000 driver: USB Audio usb-ID: 001-006 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-25-generic
Network:   Card: Intel Ethernet Connection (2) I218-V driver: e1000e ver: 2.3.2-k port: f040 bus-ID: 00:19.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: d0:50:99:28:ed:16
Drives:    HDD Total Size: 1120.2GB (38.5% used) 1: id: /dev/sda model: INTEL_SSDSC2CW12 size: 120.0GB temp: 0C 
           2: id: /dev/sdb model: WDC_WD10EZEX size: 1000.2GB temp: 45C 
Partition: ID: / size: 103G used: 7.2G (8%) fs: ext4 ID: swap-1 size: 8.53GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 47.0C mobo: N/A gpu: 0.0:46C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 219 Uptime: 8 min Memory: 1652.6/7933.0MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17
```

---

### Post by DJDBgr on 2015-08-15
For the record, i solved this by adding [COLOR=#111111][FONT=Ubuntu]{ ForceCompositionPipeline = On } on my xorg.conf.

[/FONT][/COLOR]```
Option         "metamodes" "DVI-I-0: 1920x1080_60 +1600+0 { ForceCompositionPipeline = On }, HDMI-0: 1600x900_60 +0+0 { ForceCompositionPipeline = On }"
```

---

