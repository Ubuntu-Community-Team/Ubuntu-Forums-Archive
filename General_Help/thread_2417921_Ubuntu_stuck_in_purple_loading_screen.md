---
title: "Ubuntu stuck in purple loading screen"
date: 2019-04-29
forum: General Help
---

### Post by paul-knopf56 on 2019-04-29
Hi,

after shutting down my laptop and booting it again, I get stuck in the purple loading screen. When pressing esc it shows me :

[ OK ] Mounted /boot/efi

as last entry, but after that it doesn't seem to do anything and i can't write anything here either.

Thanks for your help!

By the way English isn't my native language, so excuse mistakes please.

---

### Post by kc1di on 2019-05-01
When you get to the desktop please go to a terminal and type this command ```
sudo apt install inxi 
``` When that finishes type ```
inxi -Fxz
```
and post the output here.

---

### Post by paul-knopf56 on 2019-05-01
Ok managed to get to the desktop, 

here is the output after running ```
inxi -Fxz
```

```
System:    Host: 404 Kernel: 4.18.0-18-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.3 (Gtk 3.22.30-1ubuntu2) Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: LENOVO product: 20DH000XGE v: ThinkPad E555 serial: N/A
           Mobo: LENOVO model: 20DH000XGE serial: N/A UEFI: LENOVO v: HTET39WW (1.11 ) date: 12/19/2014
Battery    BAT0: charge: 40.4 Wh 100.1% condition: 40.4/47.5 Wh (85%)
           model: SANYO LNV-45N1 status: Not charging
CPU:       Quad core AMD A10-7300 Radeon R6 10 Compute Cores 4C+6G (-MCP-) 
           arch: Steamroller rev.1 cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 15171
           clock speeds: max: 1900 MHz 1: 1157 MHz 2: 1128 MHz 3: 1240 MHz 4: 1260 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Kaveri [Radeon R6 Graphics] bus-ID: 00:01.0
           Card-2: Advanced Micro Devices [AMD/ATI] Jet XT [Radeon R5 M240] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.1 ) drivers: radeon,radeon Resolution: 1366x768@60.02hz
           OpenGL: renderer: AMD KAVERI (DRM 2.50.0, 4.18.0-18-generic, LLVM 7.0.0)
           version: 4.5 Mesa 18.2.8 Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel bus-ID: 00:14.2
           Card-2 Advanced Micro Devices [AMD/ATI] Kaveri HDMI/DP Audio Controller
           driver: snd_hda_intel bus-ID: 00:01.1
           Sound: Advanced Linux Sound Architecture v: k4.18.0-18-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Realtek RTL8723BE PCIe Wireless Network Adapter
           driver: rtl8723be port: 1000 bus-ID: 04:00.0
           IF: wlp4s0 state: up mac: <filter>
Drives:    HDD Total Size: 1000.2GB (1.2% used)
           ID-1: /dev/sda model: WDC_WD10SPCX size: 1000.2GB temp: 36C
Partition: ID-1: / size: 916G used: 11G (2%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 52.1C mobo: N/A gpu: 47.0,52.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 251 Uptime: 14 min Memory: 1135.0/6920.9MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.191) inxi: 2.3.56 

```

By the way after going into Ubuntu recovery mode and continuing to the desktop with ```
ctrl-D
``` I can now boot without any visible issues although it asks to send a report after a fresh boot.

thanks for you reply :)

---

### Post by dino99 on 2019-05-01
Its time to glance at warnings/errors via 'journalctl' into a terminal  :p

---

### Post by paul-knopf56 on 2019-05-01
OK done, its quite a lot I stoped looking at it after line 758 I'm guessing you don't want me to post all of it. Is there something specific you want me to look for. 
Maybe all red line or something :D

If it is here are the first that i found:

```
Apr 24 14:01:08 404 kernel: do_IRQ: 1.55 No irq handler for vector
Apr 24 14:01:08 404 kernel:  #2
Apr 24 14:01:08 404 kernel: do_IRQ: 2.55 No irq handler for vector
Apr 24 14:01:08 404 kernel:  #3
Apr 24 14:01:08 404 kernel: do_IRQ: 3.55 No irq handler for vector

```

---

