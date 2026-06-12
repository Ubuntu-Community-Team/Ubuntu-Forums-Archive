---
title: "[kubuntu] lock screen comes on during video playback"
date: 2018-06-05
forum: General Help
---

### Post by snafu- on 2018-06-05
How do I stop the lock screen coming coming on during a video? 
[HTML]z
System:    Host: snafu-Inspiron-3521 Kernel: 4.15.0-22-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: KDE Plasma 5.12.5 (Qt 5.9.5) Distro: Ubuntu 18.04 LTS
Machine:   Device: portable System: Dell product: Inspiron 3521 v: A14 serial: N/A
           Mobo: Dell model: 0010T1 v: A00 serial: N/A
           UEFI: Dell v: A14 date: 07/31/2015
Battery    BAT1: charge: 22.8 Wh 100.0% condition: 22.8/66.6 Wh (34%)
           model: LGC DELL 0MF6932F status: Full
CPU:       Dual core Intel Core i5-3337U (-MT-MCP-) 
           arch: Ivy Bridge rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 7183
           clock speeds: max: 2700 MHz 1: 1037 MHz 2: 809 MHz 3: 926 MHz 4: 944 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1280x720@60.00hz, 1280x720@60.00hz
           OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile
           version: 4.2 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Intel 7 Series/C216 Family High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-22-generic
Network:   Card-1: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 01:00.0
           IF: enp1s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
           Card-3: Atheros usb-ID: 001-006
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1000.2GB (1.9% used)
           ID-1: /dev/sda model: ST1000LM024_HN size: 1000.2GB
Partition: ID-1: / size: 914G used: 18G (2%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 705M used: 145M (23%) fs: ext4 dev: /dev/sda2
           ID-3: swap-1 size: 1.02GB used: 0.00GB (0%) fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 46.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 4700
Info:      Processes: 207 Uptime: 3:04 Memory: 1186.2/3825.8MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.191) inxi: 2.3.56 
[/HTML]

---

### Post by kazakore on 2018-06-05
What screenlocker/screensaver does Kubuntu use as standard?? (kscreensaver seem to be an answer through searching but packages in Ubuntu don't seem to quite match this.)

The only one I've managed to get to reliably work on Studio is xscreensaver.

I may have missed some but you need to remove any that are in use (a package manager like Synaptic may make it easier and search for "saver" and "locker" or similar.)

Once you have removed the default install both xscreensaver and xssproxy and configure as desired. xssproxy is the package I found needed to get it to not lock when a fullscreen program is active, with just xscreensaver it was still locking while playing videos etc.

It's also the only one I've found which doesn't give me funny issues of touchpad or keyboard randomly locking up on logging back in.

---

