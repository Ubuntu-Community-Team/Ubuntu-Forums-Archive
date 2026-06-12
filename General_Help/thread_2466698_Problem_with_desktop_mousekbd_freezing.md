---
title: "Problem with desktop mouse/kbd freezing"
date: 2021-09-03
forum: General Help
---

### Post by billytrip on 2021-09-03
I am having trouble with Ubuntu.  About once a day my desktop will freeze.  Mouse and keyboard ignored.  The system is still running, if for example I am playing an mp3 that will continue normally.  I've tried letting it sit for a while, so far once it freezes it is not coming back until reboot.

I am running 21.04 and I install every update that is suggested.  GNOME version 3.38.5.  AMD 6-core 64bit. I have tried narrowing to an application by not starting it in successive reboots.  I have eliminated Firefox, Brave, Clementine and other apps as the possible cause.  

I am reasonably technical, being a software engineer for 30+ years.  But I have no idea how to go about figuring out why I am having to reboot every day.  It's not the end of the world, so far I have never lost data and a boot takes less than 3 minutes, but I would rather not have to keep dealing with this.

Ideas on how to isolate/correct the problem?

---

### Post by ajgreeny on 2021-09-03
Let's see your full hardware report with output of terminal command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by billytrip on 2021-09-04
thanks for taking a look at my
inxi dump:

```

System:
  Kernel: 5.11.0-31-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 
  Desktop: GNOME 3.38.4 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Desktop Mobo: ASRock model: 990FX Killer serial: <filter> 
  BIOS: American Megatrends v: P1.00 date: 12/06/2013 
Battery:
  Device-1: hidpp_battery_0 model: Logitech Wireless Keyboard 
  charge: 55% (should be ignored) status: Discharging 
CPU:
  Info: 6-Core model: AMD FX-6350 bits: 64 type: MCP arch: Bulldozer rev: 0 
  L2 cache: 2 MiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 46698 
  Speed: 1535 MHz min/max: 1400/3900 MHz boost: enabled Core speeds (MHz): 
  1: 1535 2: 1452 3: 1396 4: 1395 5: 1396 6: 1395 
Graphics:
  Device-1: NVIDIA GF108 [GeForce GT 620] vendor: eVga.com. driver: nouveau 
  v: kernel bus ID: 01:00.0 
  Display: wayland server: X.Org 1.21.1.1 compositor: gnome-shell driver: 
  loaded: modesetting unloaded: fbdev,vesa resolution: 1: 1920x1080~60Hz 
  2: 1920x1080~60Hz 
  OpenGL: renderer: NVC1 v: 4.3 Mesa 21.0.3 direct render: Yes 
Audio:
  Device-1: AMD SBx00 Azalia vendor: ASRock driver: snd_hda_intel v: kernel 
  bus ID: 00:14.2 
  Device-2: NVIDIA GF108 High Definition Audio vendor: eVga.com. 
  driver: snd_hda_intel v: kernel bus ID: 01:00.1 
  Device-3: Logitech Webcam C310 type: USB driver: snd-usb-audio,uvcvideo 
  bus ID: 8-4.2:5 
  Sound Server: ALSA v: k5.11.0-31-generic 
Network:
  Device-1: Qualcomm Atheros Killer E220x Gigabit Ethernet vendor: ASRock 
  driver: alx v: kernel port: d000 bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: TP-LINK TG-3468 driver: r8169 v: kernel port: c000 bus ID: 06:00.0 
  IF: enp6s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
  IF-ID-1: tun0 state: unknown speed: 10 Mbps duplex: full mac: N/A 
Drives:
  Local Storage: total: 4.55 TiB used: 4.17 TiB (91.7%) 
  ID-1: /dev/sda vendor: Toshiba model: DT01ACA100 size: 931.51 GiB 
  ID-2: /dev/sdb vendor: Western Digital model: WD40EFZX-68AWUN0 
  size: 3.64 TiB 
Partition:
  ID-1: / size: 86.61 GiB used: 57.07 GiB (65.9%) fs: ext4 dev: /dev/sda5 
Swap:
  ID-1: swap-1 type: partition size: 9.54 GiB used: 43.6 MiB (0.4%) 
  dev: /dev/sda6 
Sensors:
  System Temperatures: cpu: 27.9 C mobo: N/A gpu: nouveau temp: 47.0 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 465 Uptime: 23h 59m Memory: 15.59 GiB used: 8.44 GiB (54.2%) 
  Init: systemd runlevel: 5 Compilers: gcc: 10.3.0 Packages: 2949 
  Shell: Bash v: 5.1.4 inxi: 3.3.01 

```

---

### Post by tea for one on 2021-09-04
```
 Device-1: NVIDIA GF108 [GeForce GT 620] vendor: eVga.com. driver: nouveau 
  v: kernel bus ID: 01:00.0 
```

No mention of Nvidia proprietary driver.
Have you tried -  Software & Updates > Additional Drivers

---

### Post by billytrip on 2021-09-04
On the Additional Drivers screen I get this:

NVIDIA Corporation: GF108 [GeForce GT 620]
This device is using an alternative driver.

There are two choices below.  the last one is "checked".

O Using NVIDIA driver metapackage from nvidia-driver-390 (proprietary, tested)
O Using X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)

Should I change something here?

---

### Post by ajgreeny on 2021-09-04
I have never used an nvidia graphic card but I think there have been and possibly still are problems using wayland graphic system, which is what you're using at the moment, with nvidia cards; some incompatibility I believe.

Try running with xorg by clicking on the cog icon at the login screen after accepting your username, and choosing "Ubuntu with xorg" to see if that helps you.

The nouveau driver currently in use is the open-source driver that has been around for many years and with wayland may be your only choice; if you use an xorg session you may be able to choose and successfully use the nvidia 390 driver listed in the choices you showed us.

---

### Post by tea for one on 2021-09-04
You can choose between Wayland and Xorg at the login screen (image attached):--

Ubuntu
Ubuntu on Wayland

---

### Post by billytrip on 2021-09-05
I am trying that now.  It definitely slows down the logon, but if it works it will be worth it.  I'll know in 2-3 days :)  Thanks everyone for your help.

---

