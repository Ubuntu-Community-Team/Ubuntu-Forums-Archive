---
title: "How to get Psensors to display GPU temps"
date: 2017-09-19
forum: General Help
---

### Post by shag00 on 2017-09-19
I am not getting any results from Psensor (Ver 1.1.5) for my GPU. Ubuntu is 17.04 and it's a Nvidia 1050 card. I have installed Psensor, lm-sensors and HDDtemp and ran "sudo sensors detect". Googling reveals that Nvidia have a utility which provides temps for the GPU but I see this as my Plan B at the moment, firstly because I am using the Ubuntu driver and secondly, I dislike vendor utilities.

Any help welcome.

---

### Post by dragonfly41 on 2017-09-19
I use GKrellM System Monitor (plus plugins) from Ubuntu Software Centre to monitor temperatures and other variables.

---

### Post by again? on 2017-09-19
When using the nouveau gfx drivers, sensors output gives me a "nouveau-pci-0100" section, 
which shows up in psensors.
My details:
```
glen@Xen2:~$ inxi -F
System:    Host: Xen2 Kernel: 4.10.0-33-generic x86_64 (64 bit) Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x Bios: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) cache: 8192 KB 
           clock speeds: max: 3800 MHz 1: 1800 MHz 2: 1800 MHz 3: 1800 MHz 4: 2600 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.19.3 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1680x1050@59.88hz
           GLX Renderer: Gallium 0.4 on NVCF GLX Version: 3.0 Mesa 17.0.7
Audio:     Card-1 NVIDIA GF116 High Definition Audio Controller driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA) driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-33-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: 74:d4:35:99:bf:f3
Drives:    HDD Total Size: 870.2GB (13.2% used) ID-1: /dev/sda model: SanDisk_SDSSDA12 size: 120.0GB
           ID-2: /dev/sdb model: WDC_WD2500AAJS size: 250.1GB ID-3: /dev/sdc model: ST3500418AS size: 500.1GB
Partition: ID-1: / size: 50G used: 33G (70%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 5.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
[COLOR="#FF0000"]Sensors:   System Temperatures: cpu: 35.0C mobo: 17.1C **gpu: 42.0**
           Fan Speeds (in rpm): cpu: 1083 fan-1: 2327 fan-3: 0[/COLOR]
Info:      Processes: 248 Uptime: 12 min Memory: 1301.5/3931.5MB Client: Shell (bash) inxi: 2.2.35
```

---

### Post by shag00 on 2017-09-21
Thank you gentlemen for your replies, in the end I ended up just installing the Nvidia driver which was quite straight forward and after a sensors-detect I have 5 GPU attributes now monitored.

---

