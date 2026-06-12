---
title: "Kernel panic on new laptop with 14.04 preinstalled"
date: 2015-09-13
forum: General Help
---

### Post by md11cf on 2015-09-13
I've been setting up a new Dell laptop with Ubuntu 14.04 preinstalled and I've been experiencing kernel panic on boot about half the time after having installed a number of programs yesterday. I was able to get two shots of the dump with a camera:

[ATTACH=CONFIG]264398[/ATTACH] [ATTACH=CONFIG]264399[/ATTACH]

Since I installed quite a few programs yesterday, this could be anything, but one issue that came up and that I thought might explain the issue is that the software updater froze in the middle of updating and configuring GRUB, which meant I had to kill the process.

I've installed boot-repair and used it to generate the following report: [http://paste.ubuntu.com/12397664/](http://paste.ubuntu.com/12397664/)

Also, here's some hardware info through inxi in case it might be useful:

```

inxi -Fxz
System:    Host: ming-Inspiron-3451 Kernel: 3.13.0-38-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Dell (portable) product: Inspiron 3451 version: A04
           Mobo: Dell model: 0H4MK6 version: A00 Bios: Dell version: A04 date: 07/07/2015
CPU:       Quad core Intel Pentium CPU N3540 (-MCP-) cache: 1024 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17334 
           Clock Speeds: 1: 2159.00 MHz 2: 2159.00 MHz 3: 2159.00 MHz 4: 2159.00 MHz
Graphics:  Card: Intel ValleyView Gen7 bus-ID: 00:02.0 
           X.Org: 1.15.1 drivers: fbdev,intel (unloaded: vesa) Resolution: 1366x768@76.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits) GLX Version: 2.1 Mesa 10.1.3 Direct Rendering: Yes
Audio:     Card: Intel ValleyView High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-38-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k bus-ID: 03:00.0
           IF: wlan0 state: up mac: <filter>
           Card-2: Atheros usb-ID: 001-007
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 500.1GB (11.3% used) 1: id: /dev/sda model: WDC_WD5000LPVX size: 500.1GB temp: 30C 
Partition: ID: / size: 448G used: 53G (13%) fs: ext4 ID: swap-1 size: 8.34GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 203 Uptime: 33 min Memory: 1752.2/3836.3MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 

```

I've also been trying to run a memory test, but I can't find a way to bring up GRUB when the computer's booting. I've read that you're supposed to hold down the shift button during the POST, but that doesn't seem to have any effect in my case.

In case the issue can't be resolved, the last resort I have is to simply restore the computer to factory settings and start over again.

Any help would be appreciated. Thanks!

---

