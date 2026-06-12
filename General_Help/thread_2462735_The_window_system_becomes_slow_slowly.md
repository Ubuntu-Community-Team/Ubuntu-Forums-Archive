---
title: "The window system becomes slow slowly"
date: 2021-05-26
forum: General Help
---

### Post by hashimus on 2021-05-26
After a while the windows becomes slow and choppy, even though my system is not under load. It feels like it doubles how slow it is the more time passes. So far i have tried to reinstall to both LTS and latest verion of ubuntu, use nouveau drivers and nvidia drivers and switching between X11 and Wayland. What i have determined so far is that the problem resets if i restart or logout.

I am currently wondering if it might be some config in my user folder which may cause it (i have /home in separate partition in case i need to reinstall).

[Here is link of what is happening https://youtu.be/a9qpjV16jfw]("https://youtu.be/a9qpjV16jfw")

---

### Post by him610 on 2021-05-27
How about providing your systems specs from a terminal using -
```
inxi -Fmxz
```
Please show results between the code tags.

---

### Post by hashimus on 2021-05-27
I am doing gpu passthrough with my GTX 650Ti in case that may be relevant.
Link to output: [https://pastebin.com/raw/HwMY6pDE](https://pastebin.com/raw/HwMY6pDE)

```

System:
  Kernel: 5.11.0-17-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 
  Desktop: GNOME 3.38.4 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Desktop System: Gigabyte product: B450M DS3H v: N/A serial: <filter> 
  Mobo: Gigabyte model: B450M DS3H-CF v: x.x serial: <filter> 
  UEFI: American Megatrends v: F50 date: 11/27/2019 
Memory:
  RAM: total: 31.37 GiB used: 4.4 GiB (14.0%) 
  RAM Report: 
  permissions: Unable to run dmidecode. Root privileges required. 
CPU:
  Info: 8-Core model: AMD Ryzen 7 3800X bits: 64 type: MT MCP arch: Zen 2 
  rev: 0 L2 cache: 4 MiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 124566 
  Speed: 2027 MHz min/max: 2200/3900 MHz boost: enabled Core speeds (MHz): 
  1: 2027 2: 4031 3: 3206 4: 3734 5: 3704 6: 3577 7: 2023 8: 2057 9: 3598 
  10: 3585 11: 3578 12: 3680 13: 2053 14: 3542 15: 2008 16: 4008 
Graphics:
  Device-1: NVIDIA GF106GL [Quadro 2000] driver: nvidia v: 390.143 
  bus ID: 05:00.0 
  Device-2: NVIDIA GK106 [GeForce GTX 650 Ti Boost] vendor: ZOTAC 
  driver: vfio-pci v: 0.2 bus ID: 06:00.0 
  Display: x11 server: X.Org 1.20.11 driver: loaded: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1: 2560x1080~60Hz 
  2: 1920x1080~60Hz 
  OpenGL: renderer: Quadro 2000/PCIe/SSE2 v: 4.6.0 NVIDIA 390.143 
  direct render: Yes 
Audio:
  Device-1: NVIDIA GF106 High Definition Audio driver: snd_hda_intel 
  v: kernel bus ID: 05:00.1 
  Device-2: NVIDIA GK106 HDMI Audio vendor: ZOTAC driver: vfio-pci v: 0.2 
  bus ID: 06:00.1 
  Device-3: AMD Starship/Matisse HD Audio vendor: Gigabyte 
  driver: snd_hda_intel v: kernel bus ID: 08:00.4 
  Device-4: Blue Microphones Yeti Stereo Microphone type: USB 
  driver: hid-generic,snd-usb-audio,usbhid bus ID: 3-4:3 
  Sound Server: ALSA v: k5.11.0-17-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Gigabyte driver: r8169 v: kernel port: e000 bus ID: 04:00.0 
  IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
  Device-2: D-Link DUB-1312 Gigabit Ethernet Adapter type: USB 
  driver: ax88179_178a bus ID: 4-1:2 
  IF: enxecade0212765 state: down mac: <filter> 
  IF-ID-1: virbr0 state: down mac: <filter> 
Drives:
  Local Storage: total: 2.26 TiB used: 868.74 GiB (37.6%) 
  ID-1: /dev/sda vendor: Western Digital model: WD10EZEX-22BN5A0 
  size: 931.51 GiB 
  ID-2: /dev/sdb vendor: Samsung model: SSD 860 EVO 1TB size: 931.51 GiB 
  ID-3: /dev/sdc vendor: Intel model: SSDSC2BB480G4 size: 447.13 GiB 
Partition:
  ID-1: / size: 58.81 GiB used: 10.03 GiB (17.1%) fs: ext4 dev: /dev/sdb3 
  ID-2: /boot/efi size: 196.9 MiB used: 14.9 MiB (7.6%) fs: vfat 
  dev: /dev/sda1 
  ID-3: /home size: 847.97 GiB used: 334.71 GiB (39.5%) fs: ext4 
  dev: /dev/sdb5 
Swap:
  ID-1: swap-1 type: partition size: 8.05 GiB used: 0 KiB (0.0%) 
  dev: /dev/sdb2 
Sensors:
  System Temperatures: cpu: 50.2 C mobo: N/A gpu: nvidia temp: 59 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 30% 
Info:
  Processes: 378 Uptime: 11m Init: systemd runlevel: 5 Compilers: 
  gcc: 10.3.0 Packages: 1979 Shell: Bash v: 5.1.4 inxi: 3.3.01 

```

---

### Post by hashimus on 2021-05-28
I think i have narrowed down the problem.

Steps i took:
I have reinstalled ubuntu on a different drive. i installed virtual machine stuff acording with this [video]("https://www.youtube.com/watch?v=tDMoEvf8Q18").
Waited some time.
Then i installed audio jack stuff acording with this [video]("https://www.youtube.com/watch?v=EoN0GLYhAzk").
Waited some time and got the issue.

Then i reinstalled ubuntu again.
Installed audio jack stuff again to confirm it's not vm stuff and it seems to be the issue.

I'm not sure exactly which package it is or how the window lagg works though.

---

