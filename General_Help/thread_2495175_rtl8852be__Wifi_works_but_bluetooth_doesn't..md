---
title: "rtl8852be | Wifi works but bluetooth doesn't."
date: 2024-02-09
forum: General Help
---

### Post by amirsaleem on 2024-02-09
I do have Realtek controller (rtl8852be) in my HP ProBook 450 15.6 inch G9 Notebook with Ubuntu 20.04, after install the OS I wasn't able to connect to wifi, I installed the driver from [https://github.com/HRex39/rtl8852be](https://github.com/HRex39/rtl8852be), and now I can use my wifi, but bluetooth still doesn't work, I tried to install it's driver from [https://github.com/HRex39/rtl8852be_bt]("https://github.com/HRex39/rtl8852be_bt?tab=readme-ov-file") , but it doesn't work for me, following are some information about my system.


>>> lspci -nnk | grep -iA3 net
    DeviceName: Onboard Ethernet
    Kernel driver in use: pcieport
00:1e.0 Communication controller [0780]: Intel Corporation Device [8086:51a8] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:8aa1]
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b852]
    Subsystem: Hewlett-Packard Company Device [103c:88e3]
    Kernel driver in use: rtl8852be
    Kernel modules: 8852be
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8aa1]
    Kernel driver in use: r8169
    Kernel modules: r8169


>>> rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

>>> lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04f3:0c7e Elan Microelectronics Corp. ELAN:ARM-M4
Bus 003 Device 003: ID 13fd:1d40 Initio Corporation PHD             
Bus 003 Device 005: ID 0bda:b85c Realtek Semiconductor Corp. Bluetooth Radio
Bus 003 Device 002: ID 05c8:0b06 Cheng Uei Precision Industry Co., Ltd (Foxlink) HP HD Camera
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


>>> inxi -Fxpmrz && lsusb && lspci && rfkill list all && mokutil --sb-state
System:    Kernel: 5.15.0-94-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.9 
           Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:   Type: Laptop System: HP product: HP ProBook 450 15.6 inch G9 Notebook PC v: N/A serial: <filter> 
           Mobo: HP model: 8AA1 v: KBC Version 21.61.00 serial: <filter> UEFI: HP v: U85 Ver. 01.07.00 
           date: 03/24/2023 
Battery:   ID-1: BAT0 charge: 40.6 Wh condition: 41.4/42.8 Wh (97%) model: Hewlett-Packard Primary 
           status: Charging 
Memory:    RAM: total: 15.27 GiB used: 5.69 GiB (37.3%) 
           RAM Report: permissions: Unable to run dmidecode. Root privileges required. 
CPU:       Topology: 6-Core model: 12th Gen Intel Core i7-1255U bits: 64 type: MT MCP arch: N/A 
           L2 cache: 12.0 MiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 62668 
           Speed: 915 MHz min/max: 400/4700 MHz Core speeds (MHz): 1: 950 2: 725 3: 842 4: 894 5: 914 6: 779 
           7: 1172 8: 1070 9: 1029 10: 1092 11: 856 12: 955 
Graphics:  Device-1: Intel vendor: Hewlett-Packard driver: i915 v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.13 driver: fbdev unloaded: modesetting,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel Graphics (ADL GT2) v: 4.6 Mesa 21.2.6 direct render: Yes 
Audio:     Device-1: Intel vendor: Hewlett-Packard driver: sof-audio-pci-intel-tgl bus ID: 00:1f.3 
           Sound Server: ALSA v: k5.15.0-94-generic 
Network:   Device-1: Realtek vendor: Hewlett-Packard driver: rtl8852be v: N/A port: 4000 bus ID: 03:00.0 
           IF: wlp3s0 state: up mac: <filter> 
           Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Hewlett-Packard 
           driver: r8169 v: kernel port: 3000 bus ID: 04:00.0 
           IF: enp4s0 state: down mac: <filter> 
           IF-ID-1: docker0 state: down mac: <filter> 
Drives:    Local Storage: total: 2.29 TiB used: 1.72 TiB (75.2%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLQ512HBLU-00BH1 size: 476.94 GiB 
           ID-2: /dev/sda type: USB vendor: Seagate model: ST2000LM007-1R8174 size: 1.82 TiB 
Partition: ID-1: / size: 467.91 GiB used: 275.65 GiB (58.9%) fs: ext4 dev: /dev/nvme0n1p2 
           ID-2: /boot/efi size: 486.0 MiB used: 6.1 MiB (1.2%) fs: vfat dev: /dev/nvme0n1p1 
           ID-3: /media/amir/Data_1 size: 319.78 GiB used: 303.47 GiB (94.9%) fs: ext4 dev: /dev/sda1 
           ID-4: /media/amir/Data_2 size: 869.80 GiB used: 661.67 GiB (76.1%) fs: ext4 dev: /dev/sda2 
           ID-5: /media/amir/Data_4 size: 549.31 GiB used: 519.97 GiB (94.7%) fs: ext4 dev: /dev/sda3 
           ID-6: /snap/bare/5 raw size: 4 KiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop0 
           ID-7: /snap/chromium-ffmpeg/34 raw size: 9.4 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop6 
           ID-8: /snap/chromium-ffmpeg/37 raw size: 14.0 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop21 
           ID-9: /snap/chromium/2742 raw size: 159.7 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop1 
           ID-10: /snap/chromium/2749 raw size: 159.7 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop5 
           ID-11: /snap/code/150 raw size: 308.2 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop2 
           ID-12: /snap/code/151 raw size: 308.2 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop29 
           ID-13: /snap/core/16202 raw size: 105.8 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop3 
           ID-14: /snap/core/16574 raw size: 105.4 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop4 
           ID-15: /snap/core18/1988 raw size: 55.5 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop9 
           ID-16: /snap/core18/2812 raw size: 55.7 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop7 
           ID-17: /snap/core20/2105 raw size: 63.9 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop22 
           ID-18: /snap/core22/1033 raw size: 74.1 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop12 
           ID-19: /snap/cups/1024 raw size: 66.5 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop10 
           ID-20: /snap/gnome-3-28-1804/198 raw size: 164.8 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop8 
           ID-21: /snap/gnome-3-34-1804/66 raw size: 219.0 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop11 
           ID-22: /snap/gnome-3-34-1804/93 raw size: 218.4 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop16 
           ID-23: /snap/gnome-42-2204/141 raw size: 497.0 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop13 
           ID-24: /snap/gtk-common-themes/1514 raw size: 64.8 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop14 
           ID-25: /snap/gtk-common-themes/1535 raw size: 91.7 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop17 
           ID-26: /snap/opera/288 raw size: 188.7 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop15 
           ID-27: /snap/opera/289 raw size: 189.5 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop26 
           ID-28: /snap/pdftk/9 raw size: 17.8 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop18 
           ID-29: /snap/scrcpy/399 raw size: 83.0 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop24 
           ID-30: /snap/snap-store/518 raw size: 51.0 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop19 
           ID-31: /snap/snap-store/959 raw size: 12.3 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop20 
           ID-32: /snap/snapd/20290 raw size: 40.9 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop28 
           ID-33: /snap/snapd/20671 raw size: 40.4 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop25 
           ID-34: /snap/vlc/3721 raw size: 321.1 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop27 
           ID-35: /snap/yt-dlp/364 raw size: 126.7 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop23 
Sensors:   System Temperatures: cpu: 47.0 C mobo: 25.0 C 
           Fan Speeds (RPM): N/A 
Repos:     Active apt repos in: /etc/apt/sources.list 
           1: deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) focal main restricted
           2: deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) focal-updates main restricted
           3: deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) focal universe
           4: deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) focal-updates universe
           5: deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) focal multiverse
           6: deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) focal-updates multiverse
           7: deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
           8: deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
           9: deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
           10: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
           11: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
           12: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
           13: deb [https://download.sublimetext.com/](https://download.sublimetext.com/) apt/stable/
           Active apt repos in: /etc/apt/sources.list.d/docker.list 
           1: deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) focal stable
           Active apt repos in: /etc/apt/sources.list.d/protonvpn-stable.list 
           1: deb [arch="all", signed-by=/usr/share/keyrings/protonvpn-stable-archive-keyring.gpg] [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable main
           Active apt repos in: /etc/apt/sources.list.d/slack.list 
           1: deb [https://packagecloud.io/slacktechnologies/slack/debian/](https://packagecloud.io/slacktechnologies/slack/debian/) jessie main
           Active apt repos in: /etc/apt/sources.list.d/tomtomtom-ubuntu-woeusb-focal.list 
           1: deb [http://ppa.launchpad.net/tomtomtom/woeusb/ubuntu](http://ppa.launchpad.net/tomtomtom/woeusb/ubuntu) focal main
           Active apt repos in: /etc/apt/sources.list.d/twingate.list 
           1: deb [trusted=yes] [https://packages.twingate.com/apt/](https://packages.twingate.com/apt/) /
Info:      Processes: 350 Uptime: 23m Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 
           inxi: 3.0.38 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04f3:0c7e Elan Microelectronics Corp. ELAN:ARM-M4
Bus 003 Device 003: ID 13fd:1d40 Initio Corporation PHD             
Bus 003 Device 005: ID 0bda:b85c Realtek Semiconductor Corp. Bluetooth Radio
Bus 003 Device 002: ID 05c8:0b06 Cheng Uei Precision Industry Co., Ltd (Foxlink) HP HD Camera
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
00:00.0 Host bridge: Intel Corporation Device 4601 (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Device 46a8 (rev 0c)
00:04.0 Signal processing controller: Intel Corporation Device 461d (rev 04)
00:06.0 PCI bridge: Intel Corporation Device 464d (rev 04)
00:06.2 PCI bridge: Intel Corporation Device 463d (rev 04)
00:08.0 System peripheral: Intel Corporation Device 464f (rev 04)
00:0d.0 USB controller: Intel Corporation Device 461e (rev 04)
00:14.0 USB controller: Intel Corporation Device 51ed (rev 01)
00:14.2 RAM memory: Intel Corporation Device 51ef (rev 01)
00:15.0 Serial bus controller [0c80]: Intel Corporation Device 51e8 (rev 01)
00:16.0 Communication controller: Intel Corporation Device 51e0 (rev 01)
00:1c.0 PCI bridge: Intel Corporation Device 51be (rev 01)
00:1c.7 PCI bridge: Intel Corporation Device 51bf (rev 01)
00:1e.0 Communication controller: Intel Corporation Device 51a8 (rev 01)
00:1e.2 Serial bus controller [0c80]: Intel Corporation Device 51aa (rev 01)
00:1f.0 ISA bridge: Intel Corporation Device 5182 (rev 01)
00:1f.3 Multimedia audio controller: Intel Corporation Device 51c8 (rev 01)
00:1f.4 SMBus: Intel Corporation Device 51a3 (rev 01)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device 51a4 (rev 01)
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd Device a809
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b852
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
SecureBoot disabled

---

