---
title: "Screen Resolution Stuck @ 640 x 480"
date: 2018-02-25
forum: General Help
---

### Post by zoe-scutterbug on 2018-02-25
Dummy here
  On Thursday night i ventured into synaptic and noticed some  recommended packages to download ... so I foolishly downloaded them  ...the next day i booted up and my screen resolution is frozen is stuck  at 640 -488. I can not see which package messed up my resolution.
  I would be very grateful for any helpful suggestions. I looked around  for solutions, one suggested deleting or editing the /etc/X11/xorg.conf  file, but I am unable to find it.
  [HTML]> System:    Host: zoe-ZBOX-EN1070-1060 Kernel: 4.13.0-36-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: MATE 1.18.0 (Gtk 3.22.25)
           Distro: Ubuntu 17.10
Machine:   Device: desktop Mobo: Motherboard by ZOTAC model: ZBOX-EN1070/1060 v: Rev.00 serial: N/A
           UEFI [Legacy]: American Megatrends v: B333P009 date: 11/08/2016
CPU:       Quad core Intel Core i5-6400T (-MCP-) 
           arch: N/A cache: 6144 KB

           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 17664
           clock speeds: max: 2800 MHz 1: 2200 MHz
           2: 2200 MHz 3: 2200 MHz 4: 2200 MHz
Graphics:  Card: NVIDIA GP104M [GeForce GTX 1070 Mobile]
           bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.5 )
           drivers: fbdev (unloaded: modesetting,vesa) FAILED: nouveau
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 5.0, 256 bits)
           version: 3.3 Mesa 17.2.8 Direct Render: Yes
Audio:     Card-1 NVIDIA GP104 High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel Sunrise Point-H HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: ALSA v: k4.13.0-36-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000
           bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full
           mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: c000
           bus-ID: 03:00.0
           IF: enp3s0 state: down mac: <filter>
           Card-3: Intel Wireless 3165
           driver: iwlwifi bus-ID: 04:00.0
           IF: wlp4s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (26.2% used)
           ID-1: /dev/sda model: Samsung_SSD_850 size: 250.1GB

           ID-2: /dev/sdb model: Samsung_SSD_850 size: 250.1GB

Partition: ID-1: / size: 37G used: 23G (66%)
           fs: ext4 dev: /dev/sda2
           ID-2: /home size: 176G used: 84G (51%)
           fs: ext4 dev: /dev/sda3
           ID-3: swap-1 size: 17.52GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 59.0C mobo: 29.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 259 Uptime: 0 min Memory: 1081.3/15997.5MB
           Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.37



zoe@zoe-ZBOX-EN1070-1060:~$ sudo lshw -c video
[sudo] password for zoe: 
  *-display                 
       description: VGA compatible controller
       product: GP104M [GeForce GTX 1070 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff

 xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480       73.00[/HTML]* 
  Any help will be much appreciated. I have attempted to nest the code but I think I may have failed. Many thanks zoe

---

### Post by Autodave on 2018-02-25
Let's start with any Nvidia driver that you installed.  IF you installed one, what one and where did you get it from?

---

### Post by dragonfly41 on 2018-02-25
This will look back at your Synaptic history ..

Launch Synaptic Package Manager.

Go to File > History > February 2018.

Inspect Thursday 22nd Feb.

...


In command terminal run .. arandr

set Outputs > Resolution

---

### Post by zoe-scutterbug on 2018-02-25
> **Autodave said:**
> Let's start with any Nvidia driver that you installed.  IF you installed one, what one and where did you get it from?

  	 	 	 	   Through the standard source, I think. Synaptic says I am using the recommended driver,  on the night of the 23[SUP]rd[/SUP] one of the ‘missing or recommended' things I downloaded from synaptic was I am sure was something to do with nvidia but cant see anything in my synaptic history.

---

### Post by zoe-scutterbug on 2018-02-25
> **dragonfly41 said:**
> This will look back at your Synaptic history ..

Launch Synaptic Package Manager.

Go to File > History > February 2018.

Inspect Thursday 22nd Feb.

                        [HTML]

  Commit Log for Fri Feb 23 01:25:03 2018
 Upgraded the following packages:
 cpp-7 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2
 g++-7 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 gcc-7 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2
 gcc-7-base (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 gcc-7-base:i386 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2
 gfortran-7 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2
 lib32gcc1 (1:7.2.0-8ubuntu3) to 1:7.2.0-8ubuntu3.2 libasan4 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2
 libatomic1 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2
 libcc1-0 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libcephfs2 (12.2.1-0ubuntu0.17.10.1) to 12.2.2-0ubuntu0.17.10.1
 libcilkrts5 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2
 libgcc-7-dev (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libgcc1 (1:7.2.0-8ubuntu3) to 1:7.2.0-8ubuntu3.2
 libgcc1:i386 (1:7.2.0-8ubuntu3) to 1:7.2.0-8ubuntu3.2
 libgfortran-7-dev (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2
 libgfortran4 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libgomp1 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libitm1 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 liblsan0 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libmpx2 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2
 libobjc4 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libpulse-mainloop-glib0 (1:10.0-2ubuntu3) to 1:10.0-2ubuntu3.1
 libpulse0 (1:10.0-2ubuntu3) to 1:10.0-2ubuntu3.1 libpulse0:i386 (1:10.0-2ubuntu3) to 1:10.0-2ubuntu3.1
 libpulsedsp (1:10.0-2ubuntu3) to 1:10.0-2ubuntu3.1 libquadmath0 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 librados2 (12.2.1-0ubuntu0.17.10.1) to 12.2.2-0ubuntu0.17.10.1 libstdc++-7-dev (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libstdc++6 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libstdc++6:i386 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libtsan0 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libubsan0 (7.2.0-8ubuntu3) to 7.2.0-8ubuntu3.2 libwavpack1 (5.1.0-2ubuntu0.1) to 5.1.0-2ubuntu0.2 ntp (1:4.2.8p10+dfsg-5ubuntu3.1) to 1:4.2.8p10+dfsg-5ubuntu3.2 pulseaudio (1:10.0-2ubuntu3) to 1:10.0-2ubuntu3.1
 pulseaudio-module-bluetooth (1:10.0-2ubuntu3) to 1:10.0-2ubuntu3.1 pulseaudio-module-gconf (1:10.0-2ubuntu3) to 1:10.0-2ubuntu3.1 pulseaudio-utils (1:10.0-2ubuntu3) to 1:10.0-2ubuntu3.1 sntp (1:4.2.8p10+dfsg-5ubuntu3.1) to 1:4.2.8p10+dfsg-5ubuntu3.2
 

  Commit Log for Fri Feb 23 01:29:19 2018 Removed the following packages: sessioninstaller Installed the following packages: apport-gtk (2.20.7-0ubuntu3.7) bumblebee (3.2.1-16) catfish (1.4.2-0ubuntu2) gedit (3.22.1-1ubuntu1)
 gedit-common (3.22.1-1ubuntu1) gnome-session-flashback (1:3.26.0-1ubuntu1) gnome-software (3.26.1-0ubuntu2.17.10.1) gnome-software-common (3.26.1-0ubuntu2.17.10.1)
 gnome-software-plugin-snap (3.26.1-0ubuntu2.17.10.1) libreoffice-wiki-publisher (1.2.0+LibO6.0.1~rc1-0ubuntu0.17.10.1~lo1) libsnapd-glib1 (1.23-0ubuntu1) primus (0~20150328-4) primus-libs (0~20150328-4)
 primus-libs-ia32:i386 (0~20150328-4)
 primus-libs:i386 (0~20150328-4)
 snapd-login-service (1.23-0ubuntu1)
[/HTML][INDENT]then some failed attempts to sort it

 [/INDENT]
[HTML]Commit Log for Fri Feb 23 22:24:33 2018
 Removed the following packages: gnome-software gnome-software-plugin-snap 

  Installed the following packages: sessioninstaller (0.20+bzr150-0ubuntu4.1) Commit Log for Fri Feb 23 23:02:40 2018 
  Reinstalled the following packages: nvidia-384 (384.111-0ubuntu0.17.10.1)[/HTML]  



...

> **dragonfly41 said:**
> 
In command terminal run .. arandr

set Outputs > Resolution

Downloaded app...but still only offers me the 640 x 480.

thanks zoe

---

### Post by zoe-scutterbug on 2018-02-25
YAYE fixed ...remembered ..copying and pasting my synaptic downloads  I spotted Bumblebee ...which i half remembered another post mentioning it

Removed Bumblebee Problem solved

---

