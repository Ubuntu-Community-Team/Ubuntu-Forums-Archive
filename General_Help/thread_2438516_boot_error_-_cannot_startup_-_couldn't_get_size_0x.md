---
title: "boot error - cannot startup - couldn't get size: 0x800000000000000e"
date: 2020-03-13
forum: General Help
---

### Post by linuxlobo on 2020-03-13
Hi,
Unfortunately, I can't get past the following text displayed on boot up of Linux mint:

(Note: there may be small typos in the following two code blocks as I copied the outputs by hand)

Code: Select all

[    0.163747] platform MSFT01010: failed to claim resource 1 [men 0xfed40000 - 0xfed40fff]
[    0.163754] acpi MSFT0101:00: platform device creation failed: -16
[    1.363134] couldn't get size: 0x800000000000000e

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(Initramfs) 

At this point I typed <exit>and received:

Code: Select all

Gave up waiting for root file system device. Common problems:
- boot args (cat /proc/cmdline)
 - check root delay= (did the system wait long enough?)
- missing modules (cat /proc/modules; 1s /dev)
ALERT! /dev/mapper/mint--vg-root does not exist. Dropping to a shell! 

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(Initramfs)

I tried to use TimeShift with the live CD to restore the last backup available but have the same error message. Details of my system are listed below FYI:

Apologies the topic's title isn't that specific ...its hard to know what error line to use. :?
I have recently been kindly advised that it's a bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1743908](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1743908)

I have tried rebooting with secure boot enabled but still no luck as this seems to have worked in the past :(

Any assistance would be greatly appreciated on how to get this error or bug fixed. I'm really lost on what to do.

Code: Select all

mint@mint:~$ inxi -Fxxxrz
System:    Host: mint Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Cinnamon 3.8.8 (Gtk 3.22.30-1ubuntu1) dm: lightdm
           Distro: Linux Mint 19 Tara
Machine:   Device: laptop System: LENOVO product: 80SW v: Lenovo ideapad 710S-13ISK serial: N/A
           Mobo: LENOVO model: Lenovo ideapad 710S-13ISK v: SDK0J40709 WIN serial: N/A
           UEFI: LENOVO v: 0NCN41WW date: 03/15/2018
           Chassis: type: 10 v: Lenovo ideapad 710S-13ISK serial: N/A
Battery    BAT0: charge: 22.1 Wh 100.1% condition: 22.1/46.0 Wh (48%)
           volts: 8.4/7.6
           model: LGC L15L4PC0 Li-poly serial: <filter>status: Full cycles: 0
CPU:       Dual core Intel Core i7-6560U (-MT-MCP-) 
           arch: Skylake rev.3 cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8832
           clock speeds: min/max: 400/3200 MHz 1: 1300 MHz 2: 1300 MHz
           3: 1300 MHz 4: 1300 MHz
Graphics:  Card: Intel Iris Graphics 540 bus-ID: 00:02.0 chip-ID: 8086:1926
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.01hz, 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel Iris Graphics 540 (Skylake GT3e)
           version: 4.5 Mesa 18.0.0-rc5 (compat-v: 3.0) Direct Render: Yes
Audio:     Card Intel Sunrise Point-LP HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3 chip-ID: 8086:9d70
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Intel Wireless 8260
           driver: iwlwifi bus-ID: 01:00.0 chip-ID: 8086:24f3
           IF: wlp1s0 state: up mac: <filter>
Drives:    HDD Total Size: NA (-)
           ID-1: /dev/nvme0n1 model: SAMSUNG_MZVLV256HCHP size: 256.1GB
           serial: <filter> firmware: 5L0QBXV7
           ID-2: USB /dev/sda model: USB_Flash_Disk size: 8.1GB
           serial: <filter> temp: 0C
Partition: ID-1: / size: 3.7G used: 85M (3%) fs: overlay dev: N/A
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 38.5C mobo: 37.0C
           Fan Speeds (in rpm): cpu: N/A
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb cdrom:[Linux Mint 19 _Tara_ - Release amd64 20180717]/ bionic contrib main non-free
           Active apt sources in file: /etc/apt/sources.list.d/official-package-repositories.list
           deb [http://packages.linuxmint.com](http://packages.linuxmint.com) tara main upstream import backport #id:linuxmint_main
           deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted universe multiverse
           deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main restricted universe multiverse
           deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse
           deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security main restricted universe multiverse
           deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) bionic partner
Info:      Processes: 202 Uptime: 19 min Memory: 1561.2/7561.5MB
           Init: systemd v: 237 runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191 running in gnome-terminal-) inxi: 2.3.56

---

