---
title: "Ubuntu 19.04 desktop freezes"
date: 2019-07-07
forum: General Help
---

### Post by tech291083 on 2019-07-07
Hi Friends,


I just installed the latest Ubuntu 19.04 Desktop on one of my hard drives. I have multiple hard drives with each of them only having a particular OS installed on it such as Ubuntu, Fedora, Windows 7 and CentOS. I am found of learning something about the various OS out there. My exact Ubuntu OS is as follows. It is 64 bit.


ubuntu-19.04-desktop-amd64.iso


I downloaded it from the following URL, checksums also matched so I wrote the iso to a brand new DVD and installed it without any issues whatsoever.


[http://releases.ubuntu.com/19.04/](http://releases.ubuntu.com/19.04/)



Now, when I start my PC, Ubuntu boots, but freezes and the freeze never comes to an end the screen goes totally blank, but the PC remains on. My PC is in perfect working order and all the other hard drives and operating systems installed on them work fine, but Ubuntu is the only one giving me issues, despite an error free clean install. Can you please guide me?

Thanks a lot.

My motherboard is Gigabyte H61M-S.


[https://www.gigabyte.com/in/Motherboard/GA-H61M-S-rev-10#ov](https://www.gigabyte.com/in/Motherboard/GA-H61M-S-rev-10#ov)



I am trying to give you as much info as possible about the hardware profile of my PC, which is given below as output of various commands.

```

[root@localhost james]# inxi -Fx
System:    Host: localhost.localdomain Kernel: 5.0.4-200.fc29.x86_64 x86_64 bits: 64 compiler: gcc v: 8.3.1 Console: tty 0 
           Distro: Fedora release 29 (Twenty Nine) 
Machine:   Type: Desktop Mobo: Gigabyte model: H61MS v: x.x serial: N/A BIOS: American Megatrends v: F3 date: 09/23/2016 
CPU:       Topology: Dual Core model: Intel Core i3-3220 bits: 64 type: MT MCP arch: Ivy Bridge rev: 9 L2 cache: 3072 KiB 
           flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 26340 
           Speed: 1596 MHz min/max: 1600/3300 MHz Core speeds (MHz): 1: 1596 2: 1597 3: 1596 4: 1597 
Graphics:  Device-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics vendor: Gigabyte driver: i915 v: kernel 
           bus ID: 00:02.0 
           Display: server: X.org 1.20.4 driver: i915 tty: 158x44 
           Message: Advanced graphics data unavailable for root. 
Audio:     Device-1: Intel 6 Series/C200 Series Family High Definition Audio vendor: Gigabyte driver: snd_hda_intel v: kernel 
           bus ID: 00:1b.0 
           Sound Server: ALSA v: k5.0.4-200.fc29.x86_64 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Gigabyte driver: r8169 v: kernel 
           port: e000 bus ID: 02:00.0 
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: e0:d5:5e:08:9c:1d 
           IF-ID-1: virbr0 state: down mac: 52:54:00:e1:cd:48 
           IF-ID-2: virbr0-nic state: down mac: 52:54:00:e1:cd:48 
Drives:    Local Storage: total: 465.76 GiB used: 246.35 GiB (52.9%) 
           ID-1: /dev/sda vendor: Seagate model: ST3500414CS size: 465.76 GiB temp: 36 C 
Partition: ID-1: / size: 48.97 GiB used: 36.37 GiB (74.3%) fs: ext4 dev: /dev/dm-0 
           ID-2: /boot size: 975.9 MiB used: 218.9 MiB (22.4%) fs: ext4 dev: /dev/sda1 
           ID-3: /home size: 399.56 GiB used: 209.76 GiB (52.5%) fs: ext4 dev: /dev/dm-2 
           ID-4: swap-1 size: 7.81 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-1 
Sensors:   System Temperatures: cpu: 40.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 238 Uptime: 49m Memory: 7.69 GiB used: 1.36 GiB (17.6%) Init: systemd runlevel: 5 Compilers: gcc: 8.3.1 
           Shell: bash v: 4.4.23 inxi: 3.0.34 
[root@localhost james]# 

```

```

[root@localhost james]# hwinfo --short
cpu:                                                            
                       Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz, 1639 MHz
                       Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz, 1650 MHz
                       Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz, 1625 MHz
                       Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz, 1641 MHz
keyboard:
  /dev/input/event3    Holtek Keyboard LKS02
mouse:
  /dev/input/mice      Logitech M105 Optical Mouse
monitor:
                       L9W
4
graphics card:
                       Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
sound:
                       Intel 6 Series/C200 Series Chipset Family High Definition Audio Controller
storage:
                       Intel 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller
                       Intel 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller
network:
  enp2s0               Gigabyte Onboard Ethernet
network interface:
  virbr0               Ethernet network interface
  lo                   Loopback network interface
  virbr0-nic           Ethernet network interface
  enp2s0               Ethernet network interface
disk:
  /dev/sda             ST3500414CS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVDRAM GH24NSC0
usb controller:
                       Intel 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
                       Intel 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
bios:
                       BIOS
bridge:
                       Intel 6 Series/C200 Series Chipset Family PCI Express Root Port 1
                       Intel H61 Express Chipset Family LPC Controller
                       Intel Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
                       Intel 6 Series/C200 Series Chipset Family PCI Express Root Port 5
hub:
                       Intel Integrated Rate Matching Hub
                       Linux Foundation 2.0 root hub
                       Intel Integrated Rate Matching Hub
                       Linux Foundation 2.0 root hub
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
                       Intel 6 Series/C200 Series Chipset Family MEI Controller #1
                       Intel 6 Series/C200 Series Chipset Family SMBus Controller
  /dev/input/event5    Holtek Keyboard LKS02
[root@localhost james]# 

```

```

[root@localhost james]# lshw -short
H/W path             Device      Class          Description
===========================================================
                                 system         To be filled by O.E.M. (To be filled by O.E.M.)
/0                               bus            H61MS
/0/0                             memory         64KiB BIOS
/0/4                             memory         64KiB L1 cache
/0/5                             memory         512KiB L2 cache
/0/6                             memory         3MiB L3 cache
/0/7                             memory         8GiB System Memory
/0/7/0                           memory         4GiB DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/7/1                           memory         4GiB DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/43                            processor      Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz
/0/100                           bridge         Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
/0/100/2                         display        Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
/0/100/16                        communication  6 Series/C200 Series Chipset Family MEI Controller #1
/0/100/1a                        bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
/0/100/1a/1          usb1        bus            EHCI Host Controller
/0/100/1a/1/1                    bus            Integrated Rate Matching Hub
/0/100/1a/1/1/2                  input          USB Optical Mouse
/0/100/1b                        multimedia     6 Series/C200 Series Chipset Family High Definition Audio Controller
/0/100/1c                        bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 1
/0/100/1c.4                      bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 5
/0/100/1c.4/0        enp2s0      network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1d                        bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
/0/100/1d/1          usb2        bus            EHCI Host Controller
/0/100/1d/1/1                    bus            Integrated Rate Matching Hub
/0/100/1d/1/1/5                  input          USB Keyboard
/0/100/1f                        bridge         H61 Express Chipset LPC Controller
/0/100/1f.2          scsi1       storage        6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 0-3)
/0/100/1f.2/0.0.0    /dev/sda    disk           500GB ST3500414CS
/0/100/1f.2/0.0.0/1  /dev/sda1   volume         1GiB EXT4 volume
/0/100/1f.2/0.0.0/2  /dev/sda2   volume         464GiB Linux LVM Physical Volume partition
/0/100/1f.3                      bus            6 Series/C200 Series Chipset Family SMBus Controller
/0/100/1f.5          scsi2       storage        6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 4-5)
/0/100/1f.5/0.0.0    /dev/cdrom  disk           DVDRAM GH24NSC0
/0/100/1f.5/0.0.0/0  /dev/cdrom  disk           
/0/1                             system         PnP device PNP0c01
/0/2                             system         PnP device PNP0c02
/0/3                             system         PnP device PNP0b00
/0/8                             generic        PnP device INT3f0d
/0/9                             system         PnP device PNP0c02
/0/a                             system         PnP device PNP0c02
/0/b                             system         PnP device PNP0c02
/0/c                             system         PnP device PNP0c01
/1                               power          To Be Filled By O.E.M.
/2                   virbr0      network        Ethernet interface
/3                   virbr0-nic  network        Ethernet interface
[root@localhost james]# 

```

```

[root@localhost james]# lspci -v | grep "VGA" -A 12
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Gigabyte Technology Co., Ltd Device d000
	Flags: bus master, fast devsel, latency 0, IRQ 25
	Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
	Kernel modules: i915
[root@localhost james]# 

```

```

[root@localhost james]# lspci 
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 0-3) (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 4-5) (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
[root@localhost james]# 

```

---

### Post by tech291083 on 2019-07-10
Dear Friends,

I tried all I can, even changed the BIOS settings, but to no avail. I am at my wits' end. Please help. Thanks

Please have a look at the photos at the below URL showing the changes I made or the different options I tried one by one (Auto/IGFX/PEG) specially against the Init Display First parameter and each of them failed. Thanks

[https://imgur.com/a/oFCJLFv](https://imgur.com/a/oFCJLFv)

I have just uploaded a video as well just to help you understand exactly what the issue is. Many thanks.

[https://imgur.com/a/7k8jQmR](https://imgur.com/a/7k8jQmR)

---

