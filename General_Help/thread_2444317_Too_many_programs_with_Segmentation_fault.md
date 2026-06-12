---
title: "Too many programs with Segmentation fault"
date: 2020-05-28
forum: General Help
---

### Post by mvsfrasson on 2020-05-28
Hi

I am using an old laptop (Dell Latitude D530) that seems fine. I installed Xubuntu 20.04 64bits into it.
It has 3Gb RAM, HDD of 80Gb.

I have experienced Segmentation Fault on gnome-robots game (crashes in every play I do).  I reported crash to maintainer that helped me to install debug symbols for some (several) libs and programs but we could not arrive to the problem. Then Quadrapassel game also is crashing with Segmentation Fault every run.

Suspecting that it could be something on the old hardware instead of the software, I ran a build in BIOS MEMTEST and RAM passed.  Trying run GSmartControl, it crases with Segmentation Fault at startup. ](*,) I boot installation flashdrive and ran extended tests with GSmartControl from it, HD passed.

Running from flashdrive, GSmartControl run without crash, but gnome-robots crashed the same way as before.

I have a new laptop, same system Xubuntu 20.04 64bits (not sure if same libraries), same programs run without crash.

What could be causing this segmentation faults? Can it be some hardware problem, or if unlikely, how to investigate this problem?

Thanks in advance.

Miguel

---

### Post by mvsfrasson on 2020-05-28
An example of crash output from gsmartcontrol from terminal available at

[https://pastebin.com/8RmZ4DNX](https://pastebin.com/8RmZ4DNX)

---

### Post by ajgreeny on 2020-05-28
We could do with more details of your Dell Latitude D530 hardware; please show us the output from terminal command ```
inxi -Fzx
```.
I'm not a gamer at all so have no idea what the hardware requirements of your games might be, but I also suspect, like you, that this could be the main cause of the segfaults

---

### Post by mvsfrasson on 2020-05-28
Hi

I am not a gamer as well. Just some tiny games, like minesweep, for fun.

The output asked:

```
 $ inxi -Fzx
System:
  Kernel: 5.4.0-31-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Xfce 4.14.2 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Portable System: Dell product: Latitude D530 v: N/A serial: <filter> 
  Mobo: Dell model: N/A serial: <filter> BIOS: Dell v: A08 date: 12/12/2008 
Battery:
  ID-1: BAT0 charge: 26.5 Wh condition: 26.5/57.7 Wh (46%) 
  model: SMP DELL K97268 status: Full 
CPU:
  Topology: Dual Core model: Intel Core2 Duo T7250 bits: 64 type: MCP 
  arch: Core Merom rev: D L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 vmx bogomips: 7979 
  Speed: 798 MHz min/max: 800/2001 MHz Core speeds (MHz): 1: 852 2: 838 
Graphics:
  Device-1: Intel Mobile GM965/GL960 Integrated Graphics vendor: Dell 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1024x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel 965GM (CL) v: 2.1 Mesa 20.0.4 
  direct render: Yes 
Audio:
  Device-1: Intel 82801H HD Audio vendor: Dell driver: snd_hda_intel 
  v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-31-generic 
Network:
  Device-1: Broadcom and subsidiaries NetXtreme BCM5755M Gigabit Ethernet 
  PCI Express 
  vendor: Dell driver: tg3 v: 3.137 port: 10c0 bus ID: 09:00.0 
  IF: enp9s0 state: down mac: <filter> 
  Device-2: Intel PRO/Wireless 3945ABG [Golan] Network driver: iwl3945 
  v: in-tree:s port: 10c0 bus ID: 0c:00.0 
  IF: wlp12s0 state: up mac: <filter> 
  Device-3: Dell Wireless 360 Bluetooth type: USB driver: btusb 
  bus ID: 3-2:2 
Drives:
  Local Storage: total: 74.53 GiB used: 34.82 GiB (46.7%) 
  ID-1: /dev/sda vendor: Toshiba model: MK8052GSX size: 74.53 GiB 
Partition:
  ID-1: / size: 72.86 GiB used: 34.82 GiB (47.8%) fs: ext4 dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 42.0 C mobo: N/A sodimm: 25.0 C 
  Fan Speeds (RPM): cpu: 0 
Info:
  Processes: 175 Uptime: 5m Memory: 2.91 GiB used: 731.1 MiB (24.5%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.16 
  inxi: 3.0.38
```

---

### Post by dino99 on 2020-05-28
you should glance at warnings (yellow lines) and errors (red lines) into 'journalctl -b' output from a terminal: 1) before getting a crash (before using the crashing app/game); 2) then after getting a crash.

Note that your hardware is limited mainly on ram; and actual 20.04 version in 64 bits could be too heavy for such config. Try installing instead 18.04 in 32 bits to see if it runs easierly.

---

### Post by mvsfrasson on 2020-05-28
Hi

I did what you said about journalctl. Nothing suspecious before crash. After crash we get only this:
```
mai 28 18:50:21 jose-Latitude-D530 kernel: gnome-robots[2393]: segfault at 7fdf98af4a97 ip 00007fdf98af4a97 sp 00007fdf87ffe9f0 error 14 in im-cedilla.so[7fdf98af9000+1000]
mai 28 18:50:21 jose-Latitude-D530 kernel: Code: Bad RIP value.
mai 28 18:50:21 jose-Latitude-D530 systemd[1]: Created slice system-systemd\x2dcoredump.slice.
mai 28 18:50:21 jose-Latitude-D530 systemd[1]: Started Process Core Dump (PID 2394/UID 0).
mai 28 18:50:23 jose-Latitude-D530 systemd-coredump[2395]: Process 2372 (gnome-robots) of user 1000 dumped core.
                                                           
                                                           Stack trace of thread 2393:
                                                           #0  0x00007fdf98af4a97 n/a (n/a + 0x0)
mai 28 18:50:23 jose-Latitude-D530 systemd[1]: [EMAIL="systemd-coredump@0-2394-0.servic"]systemd-coredump@0-2394-0.servic[/EMAIL]e: Succeeded.
```

With 3Gb RAM it has run quite smoothly, fast, on my Xubuntu 20.04. I do just web browsing (it plays youtube videos fairly well), text editing, nothing too fancy. I would like to avoid downgrade.
I will try to run from flashdrive both versions 20.04 and 18.04 to see segfaults go way.

Thanks.

---

### Post by dragonfly41 on 2020-05-29
[Could this be related to 20.04 dropping Python 2?]("https://linuxconfig.org/install-python-2-on-ubuntu-20-04-focal-fossa-linux")

---

### Post by Yellow Pasque on 2020-05-29
> **mvsfrasson said:**
> I ran a build in BIOS MEMTEST and RAM passed.

How long (or how many passes) did you run the memtest?
How did you obtain the 20.04 ISO and put it on the USB stick? If you downloaded it directly (non-torrent), did you verify the md5 or shasum?

> **dragonfly41 said:**
> [Could this be related to 20.04 dropping Python 2?]("https://linuxconfig.org/install-python-2-on-ubuntu-20-04-focal-fossa-linux")

Huh? Can you explain the thought process behind this?

---

### Post by mvsfrasson on 2020-05-29
> How long (or how many passes) did you run the memtest?

This memtest has several patterns for writting and reading the memory, runs for about 40 minutes. I ran it twice in different days.

> How did you obtain the 20.04 ISO and put it on the USB stick? If you  downloaded it directly (non-torrent), did you verify the md5 or shasum?

Torrent. I checked md5sum. Put it with Rufus on windows.

---

### Post by dino99 on 2020-05-29
If you have installed third party sources (ppa,...) then downgrade to the genuine version (easy via synaptic); then test again after a reboot.
Otherwise that means gnome-robots is faulty, and needs a report at [https://gitlab.gnome.org/GNOME/gnome-robots/-/issues/15](https://gitlab.gnome.org/GNOME/gnome-robots/-/issues/15)

---

