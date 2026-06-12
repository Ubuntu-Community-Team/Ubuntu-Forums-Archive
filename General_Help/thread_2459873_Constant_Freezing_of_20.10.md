---
title: "Constant Freezing of 20.10"
date: 2021-03-28
forum: General Help
---

### Post by brucethedog on 2021-03-28
I have a dual boot set up of Ubuntu 20.10 and Windows 10.
I get lots of freezing of Ubuntu in recent weeks, no key combination unfreezes, needs to be hard reset. Today it hung 4 times, I had left it running no apps, and returned to find it had crashed
I cant find a common cause at all, I thought at first it was when browsing, but today it hung on copying files to a HDD.
Tried a new profile, but same issue.

I cant say for certain if this happened in 20.04. I dont think it did.

Whats the best way to investigate this? Is there a dumpfile or equivalent, or other logging?
Windows 10 has no issues at all, so could it be a bad partition? I may try running a volume check on all drives, but would need to see how to do this from Ubuntu.
I cant recall the desktop model, its an acer with 3tb drive.

Bruce

---

### Post by brucethedog on 2021-03-28
Its an [COLOR=#000000]Acer XC-704[/COLOR]

---

### Post by ajgreeny on 2021-03-28
Assuming you can get it to run for long enough please show us the output of terminal command ```
inxi -Fzx
``` which will list all your hardware.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by T6&amp;sfpER35% on 2021-03-28
[here's](https://ubuntuforums.org/showthread.php?t=2457202) another recent thread you might want to follow

---

### Post by brucethedog on 2021-03-29
```

System:
  Kernel: 5.8.0-48-generic x86_64 bits: 64 compiler: gcc v: 10.2.0 
  Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:
  Type: Desktop Mobo: Acer model: Aspire XC-704 serial: <filter> 
  UEFI: American Megatrends v: R01-B0 date: 12/31/2015 
CPU:
  Info: Quad Core model: Intel Pentium J3710 bits: 64 type: MCP 
  arch: Airmont rev: 4 L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 12800 
  Speed: 612 MHz min/max: 480/2640 MHz Core speeds (MHz): 1: 581 2: 811 
  3: 515 4: 560 
Graphics:
  Device-1: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx 
  Integrated Graphics 
  vendor: Acer Incorporated ALI driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1200~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 405 (BSW) v: 4.6 Mesa 20.2.6 
  direct render: Yes 
Audio:
  Device-1: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series 
  High Definition Audio 
  vendor: Acer Incorporated ALI driver: snd_hda_intel v: kernel 
  bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.8.0-48-generic 
Network:
  Device-1: Intel Wireless 3165 driver: iwlwifi v: kernel port: f040 
  bus ID: 02:00.0 
  IF: wlo2 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Acer Incorporated ALI driver: r8169 v: kernel port: e000 
  bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 2.73 TiB used: 32.26 GiB (1.2%) 
  ID-1: /dev/sda vendor: Western Digital model: WD30EZRX-22D8PB0 
  size: 2.73 TiB temp: 21 C 
Partition:
  ID-1: / size: 91.29 GiB used: 32.21 GiB (35.3%) fs: ext4 dev: /dev/sda7 
Swap:
  ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:
  System Temperatures: cpu: 26.8 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 249 Uptime: 6m Memory: 7.67 GiB used: 1011.2 MiB (12.9%) 
  Init: systemd runlevel: 5 Compilers: gcc: 10.2.0 Packages: 2067 
  Shell: Bash v: 5.0.17 inxi: 3.1.07
  
```

---

### Post by dragonfly41 on 2021-03-29
I note this ..

Sensors:
  System Temperatures: cpu: 26.8 C mobo: **N/A** 
  Fan Speeds (RPM): **N/A**
  
  
My reading (on Dell) is ..
Sensors:   
  System Temperatures: cpu: 35.0 C mobo: 39.0 C  
  Fan Speeds (RPM): cpu: 876 mobo: 1097 
 
...

Perhaps try installing GKrellM ..
and right click on GKrellM panel (when launched) to configure
      > Builtins > Sensors

to monitor internals. Are fans working?

---

### Post by ActionParsnip on 2021-03-29
[https://www.acer.com/ac/en/HK/content/support-product/6066?b=1](https://www.acer.com/ac/en/HK/content/support-product/6066?b=1)

May want to upgrade your BIOS

---

### Post by brucethedog on 2021-03-30
Okay have updated BIOS

so now reads as below, will try this to see if it crashes

```
System:
  Kernel: 5.8.0-48-generic x86_64 bits: 64 compiler: gcc v: 10.2.0 
  Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:
  Type: Desktop Mobo: Acer model: Aspire XC-704 serial: <filter> 
  UEFI: American Megatrends v: R01-B3 date: 03/23/2017 
CPU:
  Info: Quad Core model: Intel Pentium J3710 bits: 64 type: MCP 
  arch: Airmont rev: 4 L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 12800 
  Speed: 932 MHz min/max: 480/2640 MHz Core speeds (MHz): 1: 942 2: 914 
  3: 933 4: 937 
Graphics:
  Device-1: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx 
  Integrated Graphics 
  vendor: Acer Incorporated ALI driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1200~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 405 (BSW) v: 4.6 Mesa 20.2.6 
  direct render: Yes 
Audio:
  Device-1: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series 
  High Definition Audio 
  vendor: Acer Incorporated ALI driver: snd_hda_intel v: kernel 
  bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.8.0-48-generic 
Network:
  Device-1: Intel Wireless 3165 driver: iwlwifi v: kernel port: f040 
  bus ID: 02:00.0 
  IF: wlo2 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Acer Incorporated ALI driver: r8169 v: kernel port: e000 
  bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 2.73 TiB used: 32.31 GiB (1.2%) 
  ID-1: /dev/sda vendor: Western Digital model: WD30EZRX-22D8PB0 
  size: 2.73 TiB 
Partition:
  ID-1: / size: 91.29 GiB used: 32.25 GiB (35.3%) fs: ext4 dev: /dev/sda7 
Swap:
  ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:
  System Temperatures: cpu: 26.8 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 251 Uptime: 3m Memory: 7.68 GiB used: 1.26 GiB (16.4%) 
  Init: systemd runlevel: 5 Compilers: gcc: 10.2.0 Packages: 2067 
  Shell: Bash v: 5.0.17 inxi: 3.1.07 

```

---

### Post by brucethedog on 2021-04-04
Since upgrading BIOS, its been steady (though wont rule out for sure until more testing)
Is there a command that shows like a system log, that highlights possible freezes/lockups/crashes, to see if it ties in with times when it did have issues, and to see if anything recent?

---

