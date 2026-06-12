---
title: "firefox not working properly"
date: 2017-03-08
forum: General Help
---

### Post by tulliod on 2017-03-08
I'm new to Ubuntu. I installed a dual boot windows 10-Ubuntu 16.04 few days ago. I'm finding almost impossible to use internet with Firefox from Ubuntu, it is painfully slow and most of the pages time out. If I switch to Windows, same PC and same Wifi connection, whether I use Chrome or Firefox everything works fine.
Any help welcome
Thank you

---

### Post by Geoffrey_Arndt on 2017-03-08
Need more info (we have no Crystal Balls here at UbuForums).

Try this:   open a Terminal (ctrl+alt+t).

Then:   sudo apt install inxi

Then after it's installed - - open another terminal and input:   inxi -Fx      (please post the results)

---

### Post by Geoffrey_Arndt on 2017-03-08
Of course . . . Firefox updates came across this evening (now at 52.0).

Are any of the issues above still present after applying the update?

---

### Post by lisati on 2017-03-09
@cmcanulty: I've moved your post to your own [thread]("https://ubuntuforums.org/showthread.php?t=2355017").

---

### Post by tulliod on 2017-03-09
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: unable to locate package inxi

---

### Post by Frogs Hair on 2017-03-09
Open software and updates to enable the unchecked repositories excluding source code, then try to install the package again. Also check additional drivers for WIFI drivers.

---

### Post by tulliod on 2017-03-09
System:    Host: tullio-Lenovo-H520S Kernel: 4.8.0-36-generic x86_64 (64 bit gcc: 5.4.0)            Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.1)            Distro: Ubuntu 16.04 xenial Machine:   System: LENOVO product: 2561 v: Lenovo H520S            Mobo: LENOVO model: MAHOBAY v: Win8 STD MM DPK IPG            Bios: LENOVO v: ESKT22A date: 12/19/2012 CPU:       Dual core Intel Core i3-3220 (-HT-MCP-) cache: 3072 KB            flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 13169            clock speeds: max: 3300 MHz 1: 1975 MHz 2: 3034 MHz 3: 3061 MHz            4: 2119 MHz Graphics:  Card: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller            bus-ID: 00:02.0            Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)            Resolution: 1920x1080@60.00hz            GLX Renderer: Mesa DRI Intel Ivybridge Desktop            GLX Version: 3.0 Mesa 12.0.6 Direct Rendering: Yes Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller            driver: snd_hda_intel bus-ID: 00:1b.0            Sound: Advanced Linux Sound Architecture v: k4.8.0-36-generic Network:   Card-1: Realtek RTL8188CE 802.11b/g/n WiFi Adapter            driver: rtl8192ce port: e000 bus-ID: 02:00.0            IF: wlp2s0 state: up mac: 2c:d0:5a:43:21:57            Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller            driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 04:00.0            IF: enp4s0 state: down mac: 74:27:ea:33:a0:5b Drives:    HDD Total Size: 1000.2GB (1.2% used)            ID-1: /dev/sda model: ST1000DM003 size: 1000.2GB Partition: ID-1: / size: 17G used: 4.0G (26%) fs: ext4 dev: /dev/sda8            ID-2: swap-1 size: 8.47GB used: 0.00GB (0%) fs: swap dev: /dev/sda9 RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C            Fan Speeds (in rpm): cpu: N/A Info:      Processes: 221 Uptime: 11 min Memory: 825.5/7871.7MB            Init: systemd runlevel: 5 Gcc sys: 5.4.0            Client: Shell (bash 4.3.461) inxi: 2.2.35

---

### Post by Geoffrey_Arndt on 2017-03-09
Here is a thread from the Linux Mint forums describing how to "build" the driver     [https://forums.linuxmint.com/viewtopic.php?t=174395](https://forums.linuxmint.com/viewtopic.php?t=174395)

But frankly, these days, you can get a "plug & play" usb wireless n adapter for $10.99 USD from Amazon - the _**Panda Ultra 150 n**_ nano sized dongle (same size as a wireless mouse adapter).   Just google for it on Amazon . . it's designed to work on Linux including Ubuntu based distros.

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

