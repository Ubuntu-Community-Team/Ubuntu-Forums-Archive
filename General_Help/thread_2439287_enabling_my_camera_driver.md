---
title: "enabling my camera driver"
date: 2020-03-25
forum: General Help
---

### Post by Skaperen on 2020-03-25
a few years ago i disabled the camera driver on my laptop.  it was when i was running 16.04 or 14.04, not sure.  searches for how to do this were telling me to do modprobe -r but i distrusted that because something getting in to spy on me could reload the driver too easily with modprobe.  if they can make a camera spy hack they would know how to load the camera driver.  i eventually found or was pointed to a way to disable it at boot time that would need at least a reboot to enable it.  but i have forgotten how to do that.  i've looked around /etc and /boot but i don't even know what to look for.  i thought maybe it was the kernel command line but i see nothing special in there.  i want to enable the camera while family is isolating in their various homes.  **any ideas?**

edit:

here is what my kernel cmdline has:
```
BOOT_IMAGE=/boot/vmlinuz-5.3.0-42-generic root=UUID=5112a32e-125b-4d32-b2cd-825462d2179f ro quiet splash vt.handoff=1
```

and i just double checked BIOS SETUP.  there is no reference to the camera to disable it there.

---

### Post by Skaperen on 2020-03-26
more info:

```
System:    Host: lt2a Kernel: 5.3.0-42-generic x86_64 bits: 64 gcc: 7.4.0 Desktop: Xfce 4.12.3 (Gtk 2.24.31)
           Distro: Ubuntu 18.04.4 LTS
Machine:   Device: laptop System: System76 product: Kudu Professional v: kudp1b serial: N/A
           Mobo: System76 model: Kudu Professional v: kudp1b serial: N/A
           BIOS: American Megatrends v: 1.03.05RS762 date: 06/23/2014
Battery    BAT0: charge: 58.5 Wh 100.0% condition: 58.5/62.2 Wh (94%) model: Notebook BAT status: Full
CPU:       Quad core Intel Core i7-4710MQ (-MT-MCP-) arch: Haswell rev.3 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 19953
           clock speeds: max: 3500 MHz 1: 1294 MHz 2: 1290 MHz 3: 1347 MHz 4: 1117 MHz 5: 1305 MHz 6: 1476 MHz
           7: 1105 MHz 8: 1222 MHz
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.20.5 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile version: 4.5 Mesa 19.2.8 Direct Render: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k5.3.0-42-generic
Network:   Card-1: Intel Wireless 7260 driver: iwlwifi bus-ID: 04:00.0
           IF: wlp4s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 port: e000 bus-ID: 05:00.2
           IF: enp5s0f2 state: down mac: <filter>
Drives:    HDD Total Size: 2120.4GB (33.8% used)
           ID-1: /dev/sda model: HGST_HTS721010A9 size: 1000.2GB
           ID-2: /dev/sdb model: Samsung_SSD_840 size: 120.0GB
           ID-3: /dev/sdc model: HGST_HTS721010A9 size: 1000.2GB
Partition: ID-1: / size: 16G used: 12G (75%) fs: ext4 dev: /dev/sda1
           ID-2: /home size: 886G used: 643G (77%) fs: ext4 dev: /dev/sda4
           ID-3: swap-1 size: 17.18GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 1160 Uptime: 1 day Memory: 6238.8/15933.3MB Init: systemd runlevel: 5 Gcc sys: 7.5.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56
```

---

### Post by Skaperen on 2020-03-29
it turns out that pressing **Fn+F10** enables and disables the camera.  so i must have disabled it this way years ago.  the answer was a reply on the Linux Questions forum.  apparently the state of the camera is preserved across reboots and power cycles (done many of both over the years including a full fresh install of Xubuntu 18.04 on 1 July 2019).

---

