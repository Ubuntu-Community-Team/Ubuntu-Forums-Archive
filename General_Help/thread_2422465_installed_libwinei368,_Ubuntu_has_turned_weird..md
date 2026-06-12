---
title: "installed libwine:i368, Ubuntu has turned weird."
date: 2019-07-08
forum: General Help
---

### Post by thegurks on 2019-07-08
Hi! I hope this is the right place to post this. 

I have broken/changed/weirded out my installation of Ubuntu 18.04. It tells me a lot of my applications (including chromium, R and many more that are definitely installed) are not to be found. 


I'll try to reconstruct what happened:

1) I wanted to install wine32 to run some 32bit windows software. ```
sudo apt-get install wine32
``` replied with something like ```
wine32:i386 : Depends: libwine:i386 (something) but it is not going to be installed
```.

2) I tried to fix this problem with, I THINK, ```
sudo apt-get install libwine:i386
```, which proceeded to download and install some ~2gb of things. This was apparently a mistake.

3) After that was done, my desktop symbols were mostly broken and desktop formatting was very weird. I tried to reboot

4) ... which brought me back to commandline screen (with my tmux interface, interestingly). From here, I managed to restore the GUI with 
```

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudp apt-get install unity

```

5) After reboot, things are now seemingly fine. However, many of my applications have disappeared, e.g. Rstudio, chromium and many others (potentially all that i installed with apt-get?). Also the mouse cursor keeps getting smaller and larger depending on where it is. 

I have the feeling that I have changed something very fundamental about the system, but I can't put my finger onto it. Can anyone help me get back my applications? 


Some general info: 
```
(base) ~$ inxi -Fx
System:    Host: pc-korbel29 Kernel: 4.15.0-54-generic x86_64
           bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu3)
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: LENOVO product: 20KHCTO1WW v: ThinkPad X1 Carbon 6th serial: N/A
           Mobo: LENOVO model: 20KHCTO1WW v: SDK0J40697 WIN serial: N/A
           UEFI: LENOVO v: N23ET59W (1.34 ) date: 11/08/2018
Battery    BAT0: charge: 53.9 Wh 99.9% condition: 53.9/57.0 Wh (95%)
           model: SMP 01AV430 status: Full
CPU:       Quad core Intel Core i7-8650U (-MT-MCP-)
           arch: Kaby Lake rev.10 cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 16896
           clock speeds: max: 4200 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz
           4: 800 MHz 5: 800 MHz 6: 800 MHz 7: 800 MHz 8: 800 MHz
Graphics:  Card: Intel UHD Graphics 620 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 2560x1440@60.01hz, 1680x1050@59.88hz, 1680x1050@59.95hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2)
           version: 4.5 Mesa 18.2.2 Direct Render: Yes
Audio:     Card-1 Intel Sunrise Point-LP HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Card-2 Lenovo driver: USB Audio usb-ID: 001-011
           Sound: Advanced Linux Sound Architecture v: k4.15.0-54-generic
Network:   Card-1: Intel Ethernet Connection (4) I219-LM
           driver: e1000e v: 3.2.6-k bus-ID: 00:1f.6
           IF: enp0s31f6 state: down mac: e8:6a:64:78:63:f5
           Card-2: Intel Wireless 8265 / 8275 driver: iwlwifi bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: a0:a4:c5:91:d0:2f
Drives:    HDD Total Size: 512.1GB (23.3% used)
           ID-1: /dev/nvme0n1 model: WDC_PC_SN720_SDAQNTW size: 512.1GB
Partition: ID-1: / size: 60G used: 6.7G (12%) fs: ext4 dev: /dev/nvme0n1p3
           ID-2: /tmp size: 4.6G used: 9.5M (1%) fs: ext2 dev: /dev/nvme0n1p5
           ID-3: /var size: 19G used: 7.0G (41%) fs: ext4 dev: /dev/nvme0n1p4
           ID-4: /boot size: 473M used: 143M (32%)
           fs: ext2 dev: /dev/nvme0n1p2
           ID-5: /home size: 366G used: 79G (23%)
           fs: ext4 dev: /dev/nvme0n1p7
           ID-6: swap-1 size: 21.28GB used: 0.00GB (0%)
           fs: swap dev: /dev/nvme0n1p6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 57.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 347 Uptime: 2:26 Memory: 3751.3/15791.1MB
           Init: systemd runlevel: 5 Gcc sys: 7.4.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56
```

Thanks for any help!

---

### Post by mastablasta on 2019-07-08
well you are doing it wrong. to run 32 bit software in wine all you need to do is create wine32 prefix. 

more here: 
[https://askubuntu.com/questions/177192/how-do-i-create-a-32-bit-wine-prefix](https://askubuntu.com/questions/177192/how-do-i-create-a-32-bit-wine-prefix)
and here:
[https://wiki.winehq.org/FAQ#How_do_I_create_a_32_bit_wineprefix_on_a_64_bit_system.3F](https://wiki.winehq.org/FAQ#How_do_I_create_a_32_bit_wineprefix_on_a_64_bit_system.3F)

if you are having difficulty in using CLi i suggest using GUI such as Playonlinux (don't use the scripts as they don't work well), Lutris or Proton (requires Steam). If you need customer support and are willing to pay for it, then you can also use Crossover.

---

### Post by CatKiller on 2019-07-08
Were you using Unity before? 18.04 wouldn't have been using Unity by default; they switched to Gnome. You installed Unity after reinstalling ubuntu-desktop and I'm not sure why.

---

### Post by thegurks on 2019-07-09
I was using Gnome before. I just followed some instructions. However, also what I'm using now seems to be Gnome. I can't tell you how that happened. 
All is similar to before, just, as I said, my applications are no longer remembered.

---

