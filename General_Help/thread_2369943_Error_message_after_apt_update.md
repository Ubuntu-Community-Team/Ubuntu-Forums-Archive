---
title: "Error message after apt update"
date: 2017-08-28
forum: General Help
---

### Post by xendistar2 on 2017-08-28
I have just run 

```
sudo apt-get update && sudo apt-get dist-upgrade
```

In a terminal screen to update my current install. Part of the update  was the 4.10.0-33.37 kernel, at the end of the update and subsequent  install I got the following error

```
Setting up linux-signed-image-4.10.0-33-generic (4.10.0-33.37) ...
warning: file-aligned section .text extends beyond end of file
warning: checksum areas are greater than image size. Invalid section table?
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
```

I have not yet shutdown or rebooted the PC, is it save to do so with those errors??

Xubuntu is the only OS on the PC

PC Spec
```
System:    Host: lunar Kernel: 4.10.0-32-generic x86_64 (64 bit) Desktop: Xfce 4.12.3
           Distro: Ubuntu 17.04
Machine:   Device: desktop Mobo: ASUSTeK model: P8H61-M LE v: Rev x.0x
           UEFI: American Megatrends v: 4401 date: 08/10/2012
CPU:       Dual core Intel Core i3-2120 (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 3300 MHz 1: 1795 MHz 2: 1892 MHz 3: 1695 MHz 4: 1654 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Display Server: X.Org 1.19.3 drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Desktop GLX Version: 3.0 Mesa 17.0.7
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-32-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: 54:04:a6:a5:12:4e
Drives:    HDD Total Size: 1160.3GB (9.5% used)
           ID-1: /dev/sda model: ST500DM002 size: 500.1GB
           ID-2: /dev/sdb model: SAMSUNG_HD501LJ size: 500.1GB
           ID-3: /dev/sdc model: Hitachi_HDS72161 size: 160.0GB
Partition: ID-1: / size: 28G used: 5.4G (21%) fs: ext4 dev: /dev/sda2
           ID-2: /home size: 422G used: 18G (5%) fs: ext4 dev: /dev/sda4
           ID-3: swap-1 size: 8.28GB used: 0.03GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 231 Uptime: 15 days Memory: 4098.2/7688.5MB Client: Shell (bash) inxi: 2.3.8
```

Please, can anybody advise

---

### Post by speartip on 2017-08-29
Hi.
It seems to be complaining that you have a value set for GRUB_TIMEOUT & GRUB_HIDDEN_TIMEOUT in your grub file.
This can easily be rectified, using whatever text editor you use. If it is mousepad, then run:
```
sudo mousepad /etc/default/grub
```
You can comment out the GRUB_HIDDEN_TIMEOUT, & set GRUB_TIMEOUT as in the following:
```
GRUB_DEFAULT=0
[COLOR=#ff0000]#GRUB_HIDDEN_TIMEOUT=0[/COLOR]
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=#ff0000]GRUB_TIMEOUT=3[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""
```
Save the changes, then run:
```
sudo update-grub
```
and reboot.

---

### Post by xendistar2 on 2017-09-01
Thanks Speartip

---

