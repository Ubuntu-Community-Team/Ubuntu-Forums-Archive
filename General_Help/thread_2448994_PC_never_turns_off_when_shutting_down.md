---
title: "PC never turns off when shutting down"
date: 2020-08-17
forum: General Help
---

### Post by Magnusmaster on 2020-08-17
When I shut down my PC, the screen turns black but it never turns off (the fans keep running). I am using Ubuntu 20.04

---

### Post by mikes365 on 2020-08-18
Try to shut down via the terminal using the "Sudo power off" command

[IMG]https://vitux.com/wp-content/uploads/2019/01/word-image-35.png[/IMG]

---

### Post by Magnusmaster on 2020-08-24
I tried that but although the PC appeared to shut down the fans never stop running

---

### Post by mastablasta on 2020-08-25
please copy and paste the system specifications using code tags (the # icon in advanced answer) 
to get them you can use

```
inxi -Fz
```

or 

```
sudo lshw -sanitize
```

and also check the old logs (use log viewer or go to /var/log/ and check the logs with .old at the end) to see how the PC is shutting down and of there are any error messages. post those here as well or copy paste them to google and maybe you will find a solution.

---

### Post by guiverc on 2020-08-25
This likely doesn't apply... but it's not a device that always leaves fans running is it?

I have a box on my desk (old nokia server) which has it's fans running whenever power is connected; it's intended use was in server racks. On shutdown most fans switch off, but one always spins (at a lower speed). 

*I haven't really used it in years, but it makes a nice white-noise generator*

---

### Post by Impavidus on 2020-08-25
> **mikes365 said:**
> Try to shut down via the terminal using the "Sudo power off" command

The command is```
sudo power-off
```And if you want to post commands, please do so in code tags (like I did), not screenshots.

---

### Post by Magnusmaster on 2020-08-27
Here's the system specs. Couldn't find anything suspicious in the logs.

```
System:
  Kernel: 5.4.0-42-generic x86_64 bits: 64 Desktop: MATE 1.24.0 
  Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: Gigabyte model: H55M-S2 serial: <filter> BIOS: Award 
  v: F3 date: 07/06/2010 
CPU:
  Topology: Dual Core model: Intel Core i5 650 bits: 64 type: MT MCP 
  L2 cache: 4096 KiB 
  Speed: 1245 MHz min/max: 1197/3193 MHz Core speeds (MHz): 1: 1467 2: 1467 
  3: 1467 4: 1467 
Graphics:
  Device-1: NVIDIA GT216 [GeForce GT 220] driver: nvidia v: 340.108 
  Display: x11 server: X.Org 1.20.8 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1360x768~60Hz 
  OpenGL: renderer: GeForce GT 220/PCIe/SSE2 v: 3.3.0 NVIDIA 340.108 
Audio:
  Device-1: Intel 5 Series/3400 Series High Definition Audio 
  driver: snd_hda_intel 
  Device-2: NVIDIA GT216 HDMI Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.4.0-42-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp3s0 state: down mac: <filter> 
  Device-2: Ralink RT2561/RT61 802.11g PCI driver: rt61pci 
  IF: wlp4s2 state: up mac: <filter> 
Drives:
  Local Storage: total: 465.76 GiB used: 390.57 GiB (83.9%) 
  ID-1: /dev/sda vendor: Western Digital model: WD5000AAKS-22V1A0 
  size: 465.76 GiB 
Partition:
  ID-1: / size: 29.26 GiB used: 8.38 GiB (28.6%) fs: ext3 dev: /dev/sda6 
  ID-2: /home size: 421.71 GiB used: 381.70 GiB (90.5%) fs: ext3 
  dev: /dev/sda5 
  ID-3: swap-1 size: 7.31 GiB used: 503.2 MiB (6.7%) fs: swap dev: /dev/sda7 
Sensors:
  System Temperatures: cpu: 80.0 C mobo: N/A gpu: nvidia temp: 73 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 214 Uptime: 11h 06m Memory: 3.71 GiB used: 1.30 GiB (35.0%) 
  Shell: bash inxi: 3.0.38 
```

---

### Post by dino99 on 2020-08-28
you probably still have a running process that lock the shutdown scheduler : 
- either remove 'quet splash' from the grub menu to see what is going on when shutting down
- or glance at 'journalctl -b' output to find error(s) (red line) and warning(s) (yellow line)

---

### Post by Magnusmaster on 2020-08-28
Here is the output of journalctl -b from the last shutdown. I removed quiet splash from grub menu but nothing appears when shutting down

[https://paste.ubuntu.com/p/s5BZ97fpnt/](https://paste.ubuntu.com/p/s5BZ97fpnt/)

---

