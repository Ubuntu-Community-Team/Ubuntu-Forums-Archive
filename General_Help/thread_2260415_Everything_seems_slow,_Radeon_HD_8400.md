---
title: "Everything seems slow, Radeon HD 8400"
date: 2015-01-11
forum: General Help
---

### Post by rbwilley on 2015-01-11
Hello everyone,

    I am fairly new to linux and decided to give Ubuntu a shot.  After getting rid of the unity desk top and getting Mate up and running, I am really enjoying my experience, but there is one thing that is killing me, everything just seems slower.  I play Strife, on windows 8.1 it ran fine with lower graphic settings but since installing it on Ubuntu even when I put every setting as low as possible it is choppy.  It isn't unplayable, but I am forced to do nothing but bot games because the choppiness dampens PvP game play too much.  I have noticed this on pretty much every game I installed (DOTA2, CS:GO and CS:S through steam), where it ran fine under windows it is slow on Ubuntu, here is the spec info:

> 
System:    Host: anon Kernel: 3.13.0-43-generic i686 (32 bit, gcc: 4.8.2) Desktop: MATE 1.8.1  Distro: Ubuntu 14.04 trusty
Machine:   System: Hewlett-Packard product: 23-h052
           Mobo: Hewlett-Packard model: 2B0B version: 100 Bios: AMI version: 80.01 date: 02/11/2014
CPU:       Quad core AMD A6-5200 APU with Radeon HD Graphics (-MCP-) cache: 8192 KB flags: (lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 15969.6 
           Clock Speeds: 1: 800.00 MHz 2: 800.00 MHz 3: 1000.00 MHz 4: 800.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Kabini [Radeon HD 8400] bus-ID: 00:01.0 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@59.0hz 
           GLX Renderer: Gallium 0.4 on AMD KABINI GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes
Audio:     Card-1: Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2 
           Card-2: Advanced Micro Devices [AMD/ATI] Device 9840 driver: snd_hda_intel bus-ID: 00:01.1 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-43-generic
Network:   Card-1: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k bus-ID: 02:00.0
           IF: wlan0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: e000 bus-ID: 01:00.0
           IF: eth0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (7.4% used) 1: id: /dev/sda model: WDC_WD5000AAKX size: 500.1GB temp: 0C 
Partition: ID: / size: 455G used: 35G (9%) fs: ext4 ID: swap-1 size: 3.70GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 52.5C mobo: N/A gpu: 51.0 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 169 Uptime: 54 min Memory: 523.6/3464.7MB Runlevel: 2 Gcc sys: 4.8.2 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 



I had heard how much faster Linux was, and it is fine as long as I don't multi-task, but I need the ability to do multiple things at once.  It is especially bad if I have a game running and try to switch to a web browser or something.

---

### Post by mörgæs on 2015-01-12
Have you tried installing the closed source fglrx drivers for the GPU?

---

### Post by DuckHook on 2015-01-12
> **mörgæs said:**
> Have you tried installing the closed source fglrx drivers for the GPU?+1

The Linux open source driver (called *radeon*) is configured for stability and backward HW compatibility, and is not remotely tweaked for gaming. In fact, it tends to choke with even moderate GPU loads. On the plus side, because it does not stress the GPU, on my system at least, it runs much cooler than with *fglrx*. If gaming, *radeon* is the wrong driver.

---

### Post by Yellow Pasque on 2015-01-12
> **DuckHook said:**
> The Linux open source driver (called *radeon*) is configured for stability and backward HW compatibility, and is not remotely tweaked for gaming.

It used to be cut and dry like that, but the radeon driver is much more competitive with Catalyst on 3D performance nowadays. The version of Mesa being used is relatively old for such recent hardware.
I would suggest trying the oibaf PPA to see how the latest versions of radeon and mesa work, and of course, you can also try the proprietary driver for comparison.
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by DuckHook on 2015-01-13
> **Temüjin said:**
> ...the radeon driver is much more competitive with Catalyst on 3D performance nowadays.If this is so (and I have no reason to doubt you), then it is sweet indeed. My GPU is at least 10°C cooler with *radeon* than it is with *fglrx* and if performance is close, then the superior efficiency of *radeon* is a big plus.

Re: oibaf PPA

Did not know this PPA existed. Thanks for sharing. Another example of the power of the community.

---

### Post by pwabrahams on 2015-04-29
My machine is an HP All-in-one Pavilion g110-23, and I've tried (or think I've tried) the fglrx driver and a couple of others.  Nothing seems to cure the very sluggish performance.  I finally gave up, and I'm returning the machine to Amazon.  (To avoid hassles, I removed Linux and restored the machine to its initial state before returning it.)

---

