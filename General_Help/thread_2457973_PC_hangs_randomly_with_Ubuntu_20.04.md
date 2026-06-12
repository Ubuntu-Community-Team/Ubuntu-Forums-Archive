---
title: "PC hangs randomly with Ubuntu 20.04"
date: 2021-02-13
forum: General Help
---

### Post by Magnusmaster on 2021-02-13
My PC has been hanging randomly lately, forcing me to restart the PC every time it happens. At first I thought it was the graphics driver but it happens with both nouveau and NVIDIA drivers. I am using Ubuntu 20.04. Any help please?

---

### Post by T6&amp;sfpER35% on 2021-02-13
some more info probably needed,pls post output of ```
inxi -Fxzd
```

---

### Post by HermanAB on 2021-02-14
I would boot from install media and let it run.  If it never hangs, then you have a SW problem.  If it still hangs, then you have a HW problem.

---

### Post by Magnusmaster on 2021-02-14
> **3nd said:**
> some more info probably needed,pls post output of ```
inxi -Fxzd
```

```
System:
  Kernel: 5.4.0-65-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: MATE 1.24.0 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: Gigabyte model: H55M-S2 serial: <filter> BIOS: Award 
  v: F3 date: 07/06/2010 
CPU:
  Topology: Dual Core model: Intel Core i5 650 bits: 64 type: MT MCP 
  arch: Nehalem rev: 2 L2 cache: 4096 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 25601 
  Speed: 1467 MHz min/max: 1197/3193 MHz Core speeds (MHz): 1: 1467 2: 1466 
  3: 1467 4: 1467 
Graphics:
  Device-1: NVIDIA GT216 [GeForce GT 220] vendor: eVga.com. driver: nvidia 
  v: 340.108 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.9 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1360x768~60Hz 
  OpenGL: renderer: GeForce GT 220/PCIe/SSE2 v: 3.3.0 NVIDIA 340.108 
  direct render: Yes 
Audio:
  Device-1: Intel 5 Series/3400 Series High Definition Audio 
  vendor: Gigabyte driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Device-2: NVIDIA GT216 HDMI Audio vendor: eVga.com. driver: snd_hda_intel 
  v: kernel bus ID: 01:00.1 
  Sound Server: ALSA v: k5.4.0-65-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Gigabyte driver: r8169 v: kernel port: ce00 bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
  Device-2: Ralink RT2561/RT61 802.11g PCI driver: rt61pci v: 2.3.0 
  port: ce00 bus ID: 04:02.0 
  IF: wlp4s2 state: up mac: <filter> 
Drives:
  Local Storage: total: 465.76 GiB used: 368.45 GiB (79.1%) 
  ID-1: /dev/sda vendor: Western Digital model: WD5000AAKS-22V1A0 
  size: 465.76 GiB 
  Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVDRAM GH22NS40 rev: NL02 
  dev-links: cdrom,cdrw,dvd,dvdrw 
  Features: speed: 48 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
Partition:
  ID-1: / size: 29.26 GiB used: 10.48 GiB (35.8%) fs: ext3 dev: /dev/sda6 
  ID-2: /home size: 421.71 GiB used: 357.97 GiB (84.9%) fs: ext3 
  dev: /dev/sda5 
  ID-3: swap-1 size: 7.31 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda7 
Sensors:
  System Temperatures: cpu: 69.0 C mobo: N/A gpu: nvidia temp: 74 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 218 Uptime: 8m Memory: 3.71 GiB used: 2.00 GiB (53.9%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38 
```

---

### Post by T6&amp;sfpER35% on 2021-02-14
you still have a ext3 file system, try to upgrade it to ext4 with this [guide](https://www.howtogeek.com/424868/how-to-migrate-ext2-or-ext3-file-systems-to-ext4-on-linux/)

---

### Post by Magnusmaster on 2021-02-14
Today it hanged again. But after starting the PC again it turned off right a few seconds after boot, without even the bios screen showing up. The PC turned on and off like 5 times before booting up fine again. I still think it's a kernel problem since things got worse after a kernel update right shortly before 20.04 launched where the PC wouldn't turn off after shutting down. Linux shuts down but the PC doesn't turn off completely, the fans still run, and it still happens today. I'll see if the problem still happens with Windows.

---

### Post by DuckHook on 2021-02-14
:confused:

You have been given two pieces of excellent advice:
> **HermanAB said:**
> I would boot from install media and let it run.  If it never hangs, then you have a SW problem.  If it still hangs, then you have a HW problem.
> **3nd said:**
> you still have a ext3 file system, try to upgrade it to ext4 with this [guide](https://www.howtogeek.com/424868/how-to-migrate-ext2-or-ext3-file-systems-to-ext4-on-linux/)
Yet we have not heard back from you whether you even carried out these instructions. You cannot solve problems of these sorts by starting in the middle. You need a process of elimination.

[LIST=1]
[*]Start with HermanAB's course of action.
[*]3nd also points to an obvious problem. Ubuntu left ext3 behind years ago. That you are still using it points to either a record length string of upgrades or a flawed and very atypical install.
[*]"Thinking" that it's a kernel problem will not get you far. But aforementioned process of elimination will.
[*]Frankly, your description of symptoms screams HW to me, not SW. The way to start narrowing it down is to methodically eliminate suspects.
[/LIST]

---

### Post by mastablasta on 2021-02-16
> **Magnusmaster said:**
>  But after starting the PC again it turned off right a few seconds after boot, without even the bios screen showing up. 

so in other words PC could not even get to kernel? if that's true, then obviously nothing is wrong with kernel.

 then it's a faulty PSU or Motherboard.


also - move to ext4.

---

### Post by daniewicz on 2021-02-16
> then it's a faulty PSU or Motherboard.

Or bad RAM.

---

### Post by CelticWarrior on 2021-02-16
> **mastablasta said:**
> then it's a faulty PSU or Motherboard.
Or capacitors.

---

### Post by rbmorse on 2021-02-16
Or a thermally stressed solder joint somewhere that has gone intermittent.

---

### Post by HermanAB on 2021-02-17
I’ve even had a PC fail erratically due to a bad keyboard.  The keyboard is on the processor power bus...

---

### Post by Magnusmaster on 2021-02-17
I tried using the install media to test. It hanged once but I'm not 100% sure since the screensaver was on so the screen was black. Unfortunately I couldn't test much since Firefox crashes in the live enviroment and Ubuntu Software just plain doesn't work so I couldn't install another browser. I will try a Windows live usb (if there is such a thing) to see if it hangs with that OS 

The RAM is fine, I ran memtest86 and it passed with no errors.

---

