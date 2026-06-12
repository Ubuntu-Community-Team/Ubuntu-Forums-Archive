---
title: "Audio issues"
date: 2020-04-07
forum: General Help
---

### Post by rattbag on 2020-04-07
Hi, I'm having problems with sound on my new Ubuntu 19.10 install. Tried a lot of different things from a lot of different threads, sound didn't work on my previous install of MX Linux either,

I'm using a Toshiba Satellite S50D-A-10H. I've noticed that other people have had problems with this model on older versions of Ubuntu. It's getting quite old, I don't have an exact date but the battery is failing.

```
inxi -Fz
System:
  Host: will-SATELLITE-S50D-A-10H Kernel: 5.3.0-46-generic x86_64 bits: 64 
  Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:
  Type: Laptop System: TOSHIBA product: SATELLITE S50D-A-10H 
  v: PSKKWE-00N008EN serial: <filter> 
  Mobo: AMD model: VG10AD serial: <filter> UEFI: Insyde v: 1.30 
  date: 11/05/2013 
Battery:
  ID-1: BAT0 charge: 19.7 Wh condition: 22.1/44.4 Wh (50%) 
CPU:
  Topology: Quad Core model: AMD A8-5545M APU with Radeon HD Graphics 
  bits: 64 type: MCP L2 cache: 2048 KiB 
  Speed: 1086 MHz min/max: 1100/1700 MHz Core speeds (MHz): 1: 1091 2: 1077 
  3: 1085 4: 1092 
Graphics:
  Device-1: AMD Richland [Radeon HD 8510G] driver: radeon v: kernel 
  Device-2: AMD Sun PRO [Radeon HD 8570A/8570M] driver: radeon v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: radeon resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD ARUBA (DRM 2.50.0 / 5.3.0-46-generic LLVM 9.0.0) 
  v: 4.3 Mesa 19.2.8 
Audio:
  Device-1: AMD Trinity HDMI Audio driver: snd_hda_intel 
  Device-2: AMD FCH Azalia driver: snd_hda_intel 
  Sound Server: ALSA v: k5.3.0-46-generic 
Network:
  Device-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter 
  driver: ath9k 
  IF: wlp2s0 state: up mac: <filter> 
  Device-2: Qualcomm Atheros QCA8172 Fast Ethernet driver: alx 
  IF: enp3s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 698.64 GiB used: 7.96 GiB (1.1%) 
  ID-1: /dev/sda vendor: Toshiba model: MQ01ABD075 size: 698.64 GiB 
Partition:
  ID-1: / size: 686.18 GiB used: 7.95 GiB (1.2%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 51.8 C mobo: N/A 
  Fan Speeds (RPM): N/A 
  GPU: device: radeon temp: 50 C device: radeon temp: 56 C 
Info:
  Processes: 199 Uptime: 7m Memory: 5.02 GiB used: 1.53 GiB (30.4%) 
  Shell: bash inxi: 3.0.36 

```

---

### Post by QIII on 2020-04-07
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2439285").

Please do not hijack the threads of other users.  While your issues may seem similar with regard to symptoms, the root causes may be entirely different.  It is also confusing when people are trying to address two different issues in the same thread.

---

### Post by gsahli on 2020-04-07
install pulseaudio control (pavucontrol) - it gives you control over all devices.

---

### Post by rattbag on 2020-04-08
> Please do not hijack the threads of other users.  While your issues may  seem similar with regard to symptoms, the root causes may be entirely  different.

Apologies, I will make an effort to abide by the forum rules in future. Just seemed to be what others were doing :?

> install pulseaudio control (pavucontrol) - it gives you control over all devices.                 

Tried that already, it doesn't give me any options that bring back my sound.
[IMG]https://i.imgur.com/PBul1Ac.png[/IMG][IMG]https://i.imgur.com/FZClCLR.png[/IMG]

My audio worked fine on Win10 before switching to MX Linux then Ubuntu. I'm at the point where I'm considering switching to Fedora/Manjaro/Solus on the off chance that they work out of the box.

---

### Post by Yellow Pasque on 2020-04-08
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by rattbag on 2020-04-08
Here is the Alsa info output:[URL="http://alsa-project.org/db/?f=c45d236585d0f3bc8870a716c33f888df7797416"]

http://alsa-project.org/db/?f=c45d236585d0f3bc8870a716c33f888df7797416[/URL]

---

### Post by Yellow Pasque on 2020-04-09
Maybe this will give you some ideas? [https://bugzilla.novell.com/show_bug.cgi?id=915858](https://bugzilla.novell.com/show_bug.cgi?id=915858)
It seems like very similar hardware, a Toshiba Satellite S50D with a slightly different PCI ID (1179:fa90 vs 1179:fa91)
[https://github.com/torvalds/linux/commit/b9d9c9efc292dd0ffe172780f915ed74eba3556c](https://github.com/torvalds/linux/commit/b9d9c9efc292dd0ffe172780f915ed74eba3556c)

Sorry, I know that's probably overly technical, but maybe it will give you something to work with in a bug report instead of a generic "sound no work".

---

