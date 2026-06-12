---
title: "Screen Resolution fixed at default - failed to get gamma for output"
date: 2019-08-20
forum: General Help
---

### Post by Jonners59 on 2019-08-20
I have just got back from a few weeks leave to find a PC I always leave on had frozen and only reluctantly allowed me to move the cursor, but nothing else worked.  I had to force a restart.  After the restart the screen resolution is set at the basic 640 x 480.  I have tried resetting it in Display, but that only shows the default minimum.  I have tried in Settings Manager, but it has both the default and the display I want, but it will not save changes.  I have tried xrandr but get an error message "failed to get gamma for output"....

nvidia card and old IBM CRT screen

Ideas please for solution.  Thank you.

---

### Post by Autodave on 2019-08-20
First, please check connections at monitor and PC.  If that doesn't help, please tell us what version of 'buntu you are running, specs on your machine, and what Nvidia card you have.

---

### Post by NM5TF on 2019-08-21
@Jonners59....

if  you have an older nvidia card, you most likely need to use the open source driver nouveau rather than the nvidia driver...

I had the same problem (failed to get gamma) after nvidia dropped support for some of the older cards...switching to nouveau
fixed the resolution issue...

can you post the output of

```
inxi -F
```

tommy

---

### Post by Jonners59 on 2019-08-22
Thank you.

[PHP]inxi -F
System:
  Host: server Kernel: 5.0.0-25-generic x86_64 
  bits: 64 Desktop: Xfce 4.13.3 
  Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:
  Type: Desktop Mobo: ASUSTeK model: M5A97 LE R2.0 
  v: Rev 1.xx serial: <root required> 
  BIOS: American Megatrends v: 2006 date: 10/01/2013 
CPU:
  Topology: 8-Core model: AMD FX-8350 bits: 64 
  type: MCP L2 cache: 2048 KiB 
  Speed: 3987 MHz min/max: 1400/4000 MHz 
  Core speeds (MHz): 1: 4334 2: 4333 3: 1935 4: 1683 
  5: 4334 6: 4332 7: 1819 8: 2310 
Graphics:
  Device-1: NVIDIA GT218 [GeForce 210] driver: N/A 
  Display: x11 server: X.Org 1.20.4 
  driver: fbdev,nouveau unloaded: modesetting,vesa 
  resolution: 640x480~73Hz 
  OpenGL: renderer: llvmpipe (LLVM 8.0 128 bits) 
  v: 3.3 Mesa 19.0.8 
Audio:
  Device-1: AMD SBx00 Azalia driver: snd_hda_intel 
  Device-2: NVIDIA High Definition Audio 
  driver: snd_hda_intel 
  Device-3: Conexant Systems CX23880/1/2/3 PCI Video 
  and Audio Decoder 
  driver: cx8800 
  Device-4: Conexant Systems CX23880/1/2/3 PCI Video 
  and Audio Decoder [Audio Port] 
  driver: cx88_audio 
  Device-5: Conexant Systems CX23880/1/2/3 PCI Video 
  and Audio Decoder [MPEG Port] 
  driver: cx88-mpeg driver manager 
  Device-6: Conexant Systems CX23885 PCI Video and 
  Audio Decoder 
  driver: cx23885 
  Sound Server: ALSA v: k5.0.0-25-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express 
  Gigabit Ethernet 
  driver: r8169 
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full 
  mac: bc:ee:7b:e3:9a:79 
Drives:
  Local Storage: total: 8.41 TiB 
  used: 1.23 TiB (14.6%) 
  ID-1: /dev/sda vendor: Seagate 
  model: ST500DM002-1BD142 size: 465.76 GiB 
  ID-2: /dev/sdb vendor: Western Digital 
  model: WD40EZRZ-00GXCB0 size: 3.64 TiB 
  ID-3: /dev/sdc vendor: Western Digital 
  model: WD40EZRZ-00GXCB0 size: 3.64 TiB 
  ID-4: /dev/sdd type: USB model: TO Exter nal USB 3.0 
  size: 698.64 GiB 
Partition:
  ID-1: / size: 51.10 GiB used: 22.21 GiB (43.5%) 
  fs: ext4 dev: /dev/sda1 
  ID-2: /home size: 143.60 GiB used: 3.26 GiB (2.3%) 
  fs: ext4 dev: /dev/sda3 
  ID-3: swap-1 size: 16.54 GiB used: 33.8 MiB (0.2%) 
  fs: swap dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 42.5 C mobo: N/A 
  Fan Speeds (RPM): cpu: 0 
Info:
  Processes: 388 Uptime: 1d 14h 25m Memory: 15.56 GiB 
  used: 8.57 GiB (55.0%) Shell: bash inxi: 3.0.33 

[/PHP]

---

### Post by CatKiller on 2019-08-22
Were you using the proprietary nvidia driver prior to your lockup? Because you aren't now. The 340 branch is the last that supports that card.

---

### Post by Jonners59 on 2019-08-22
I saw that.  I do not recall.  I set it up some time ago.  I went in to Synaptics and repositories and then the video drives but it will not let me change from custom...

---

### Post by Jonners59 on 2019-08-22
any help, please???????

---

### Post by #&amp;thj^% on 2019-08-22
The only suggestion I can offer is:
```
sudo apt purge nvidia*
```
 Reboot. 
Then you should be able to install the drivers already in the official repos:
```
sudo apt install nvidia-340
``` 
And as we know, hard re-starts can cause corruption.

---

### Post by Jonners59 on 2019-08-25
> **1fallen said:**
> The only suggestion I can offer is:
```
sudo apt purge nvidia*
```
Reboot. 
Then you should be able to install the drivers already in the official repos:
```
sudo apt install nvidia-340
``` 
And as we know, hard re-starts can cause corruption.

Aghhhh...  I didn't get a notification that you had replied.  Sorry and thank you.  Been trying to fix since 06:30 this AM.  Just fixed it.....

I tried the purge and install commands but that didn't work either.  Additional Drivers would show the Nvidia and XORG drivers, but would not swap from XOrg to NVIDIA, it would just hang.  Running  ```
ubuntu-drivers devices
``` showed I was using nvidia....  So a bit more searching and playing and making things worse, esp via Synaptics I somehow managed to make it work  The last commands repeated over are below, and that seemed to fix it.


```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get autoremove
sudo apt --fix-broken install
sudo ubuntu-drivers autoinstall
```

---

