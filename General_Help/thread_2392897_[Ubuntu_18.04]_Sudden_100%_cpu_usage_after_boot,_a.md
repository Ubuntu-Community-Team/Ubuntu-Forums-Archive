---
title: "[Ubuntu 18.04] Sudden 100% cpu usage after boot, any of you experiencing the same ?"
date: 2018-05-26
forum: General Help
---

### Post by nooneelse on 2018-05-26
Sometimes when I am using Windows (for games) and then I came back to Linux after the login screen when the DM is loading Gnome it takes a lot to complete, and when it happens I notice that the CPU usage is sky high. Sometimes it's because "packagekitd", but even after killing it, the cpu usage still remains high, but now for random processes like Franz, Xorg, Gnome and so on. Since I can't kill every single process the only thing to do is reboot the machine, and everything single time it happens and then I reboot the machine, the issue disappear. Quite strange don't ? 

Is any of you experiencing the same behavior ?

Below my current config

- Dell Notebook Inspiron 15 7000 (7567)
- Ubuntu 18.04 (Updated)
- LightDM as Display Manager
- - And yes using Prime (Optimus) with NVIDIA as first option
- Proprietary NVIDIA Drivers with X.org (used "ubuntu-drivers --autoinstall" command for installation)
- Startup apps during the login: Franz, 4KStogram, sensorsp

```

bruno@funnie:[~]
> inxi -Fxz
System:    Host: funnie Kernel: 4.15.0-22-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.1 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: Dell product: Inspiron 15 7000 Gaming serial: N/A
           Mobo: Dell model: 0P84C9 v: A01 serial: N/A
           UEFI: Dell v: 1.6.0 date: 03/27/2018
Battery    BAT0: charge: 68.2 Wh 100.0% condition: 68.2/74.0 Wh (92%)
           model: SMP DELL 71JF452 status: Full
CPU:       Quad core Intel Core i7-7700HQ (-MT-MCP-) 
           arch: Skylake rev.9 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 22464
           clock speeds: max: 3800 MHz 1: 900 MHz 2: 900 MHz 3: 900 MHz
           4: 900 MHz 5: 900 MHz 6: 900 MHz 7: 900 MHz 8: 900 MHz
Graphics:  Card-1: Intel Device 591b bus-ID: 00:02.0
           Card-2: NVIDIA GP107M [GeForce GTX 1050 Ti Mobile] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting,nvidia
           Resolution: 1920x1080@60.00hz, 1600x900@59.95hz
           OpenGL: renderer: GeForce GTX 1050 Ti/PCIe/SSE2
           version: 4.6.0 NVIDIA 390.48 Direct Render: Yes
Audio:     Card Intel CM238 HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-22-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter
           driver: ath10k_pci bus-ID: 03:00.0
           IF: wlp3s0 state: down mac: <filter>
           Card-3: Atheros usb-ID: 001-005
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1256.3GB (4.9% used)
           ID-1: /dev/nvme0n1 model: WDC_WDS256G1X0C size: 256.1GB
           ID-2: /dev/sda model: TOSHIBA_MQ02ABD1 size: 1000.2GB temp: 39C
Partition: ID-1: / size: 87G used: 58G (70%) fs: ext4 dev: /dev/nvme0n1p6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 56.0C mobo: N/A gpu: 0.0:50C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 370 Uptime: 3 min Memory: 4551.4/15906.1MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56

```

```

bruno@funnie:[~]
> nvidia-smi 
Sat May 26 22:32:57 2018       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.48                 Driver Version: 390.48                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 105...  Off  | 00000000:01:00.0  On |                  N/A |
| N/A   51C    P3    N/A /  N/A |    583MiB /  4040MiB |      5%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1276      G   /usr/lib/xorg/Xorg                           320MiB |
|    0      2926      G   /usr/bin/gnome-shell                         105MiB |
|    0      3629      G   /usr/lib/4kstogram/4kstogram-bin              41MiB |
|    0      4638      G   ...-token=********************************    92MiB |
+-----------------------------------------------------------------------------+

```

```

bruno@funnie:[~]
> xrandr --listactivemonitors
Monitors: 2
 0: +*HDMI-0 1920/480x1080/270+0+0  HDMI-0
 1: +eDP-1-1 1600/344x900/194+1920+131  eDP-1-1

```

---

### Post by SL0ltMJGyh on 2018-05-27
What's your kernel version? 4.16 has been acting weird with NVIDIA-based laptops. My MSI GE60 ran ubuntu just fine until the latest kernel. I had to edit grub to fix it. I'm hearing 4.17 has similar issues too.

---

