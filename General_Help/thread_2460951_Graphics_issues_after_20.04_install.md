---
title: "Graphics issues after 20.04 install"
date: 2021-04-21
forum: General Help
---

### Post by robert48 on 2021-04-21
I've got a similar graphics issue after a freshly downloaded 20.04 AMD64 and clean installed on an Acer Inspire 3 laptop. I cannot view any video on BBC News, It reports "This content doesn't seem to be working" for any video clip I try. Codecs issue??

from inxi

```
$ inxi -Fx
System:
  Host: alison-Aspire-A315-32 Kernel: 5.8.0-50-generic x86_64 bits: 64 
  compiler: N/A Desktop: Gnome 3.36.7 
  Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: Acer product: Aspire A315-32 v: V1.10 
  serial: <superuser/root required> 
  Mobo: GLK model: Ivysaur_GL v: V1.10 serial: <superuser/root required> 
  UEFI: Insyde v: 1.10 date: 03/02/2018 
Battery:
  ID-1: BAT1 charge: 28.3 Wh condition: 33.3/37.0 Wh (90%) 
  model: PANASONIC AP16M5J status: Discharging 
CPU:
  Topology: Dual Core model: Intel Celeron N4000 bits: 64 type: MCP 
  arch: Goldmont Plus rev: 1 L2 cache: 4096 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 4377 
  Speed: 1990 MHz min/max: 800/2600 MHz Core speeds (MHz): 1: 1990 2: 1990 
Graphics:
  Device-1: Intel UHD Graphics 605 vendor: Acer Incorporated ALI 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.9 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 600 (GLK 2) v: 4.6 Mesa 20.2.6 
  direct render: Yes 
Audio:
  Device-1: Intel vendor: Acer Incorporated ALI driver: snd_hda_intel 
  v: kernel bus ID: 00:0e.0 
  Sound Server: ALSA v: k5.8.0-50-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Acer Incorporated ALI driver: r8169 v: kernel port: 1000 
  bus ID: 02:00.1 
  IF: enp2s0f1 state: down mac: d8:c4:97:7b:41:8e 
  Device-2: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter 
  vendor: Lite-On driver: ath10k_pci v: kernel port: 1000 bus ID: 03:00.0 
  IF: wlp3s0 state: up mac: 30:d1:6b:7f:77:07 
Drives:
  Local Storage: total: 931.51 GiB used: 10.18 GiB (1.1%) 
  ID-1: /dev/sda vendor: Seagate model: ST1000LM035-1RK172 size: 931.51 GiB 
  temp: 29 C 
Partition:
  ID-1: / size: 915.40 GiB used: 10.17 GiB (1.1%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 43.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 196 Uptime: 23m Memory: 3.67 GiB used: 838.8 MiB (22.3%) 
  Init: systemd runlevel: 5 Compilers: gcc: N/A Shell: bash v: 5.0.17 
  inxi: 3.0.38
```

Resolved! bad and ugly gstreamer plugins - not sure which one solved it

---

### Post by QIII on 2021-04-21
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2460766](https://ubuntuforums.org/showthread.php?t=2460766)

Please do not hijack the threads of other users.  While you may have a similar problem, the root cause may be entirely different.  Adding you post would probably have caused confusion in the thread when other users were trying to help two people.

---

### Post by robert48 on 2021-04-22
Point taken...thought it had similarities around 20.04 and might have been relevant....no intent to hijack....apologies for any offence caused.

---

