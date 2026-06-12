---
title: "Is Ubuntu becoming more and more resource-demanding than before?"
date: 2021-06-27
forum: General Help
---

### Post by josefranw on 2021-06-27
I had used ubuntu before; but I hadn't used it for a while since I did not have a computer like for 4 years. I used to like it way better than I do now.

I feel it's slower and heavier than Windows. I have a dual boot and whenever I use Windows, it logs in way faster and loads the apps and everything within seconds after having clicked on them; meanwhile, Ubuntu takes more than a minute and a half to load and when I finally can input my password to access the system, it takes another fifteen seconds or so to show the desktop and and stuff; then, to open up any app (like Chrome or LibreOffice) it takes a few more seconds (LibreOffice being the one that takes the longer...) and so happens everytime I click on an icon. The program takes a while to load and show up.

It also takes longer to log out and turn off than Windows.

Is Ubuntu becoming more and more resource-demanding than before?

---

### Post by QIII on 2021-06-27
Two things:

1. Windows uses some trickery to make it appear that it is booting faster.  It does not "shut down", but goes into a hybrid hibernation state.  It seems to boot faster, but it's not booting from nothing.  It's picking up where it left off.

2. Ubuntu (or just about any distro of Linux) boots all the way from the motherboard's POST to user interface.  Have Windows do that and your comparison would change substantially.  Or hibernate your Linux and see how that changes things.

All OSes tend to get heavier with time because we, the users, demand it.  We want more and more stuff crammed in.  However, each of us can individually remove some of the chaff from startup or completely uninstall them.  Distributors make their best guesses about what it is that the "normal" user wants to have available.  They can't make everyone happy.

My servers, with very little running, start up and reach the terminal very quickly.  A matter of seconds.  My Kubuntu takes about 20 seconds from cold boot to interface, but I have also cut out a bunch of things I don't need.

---

### Post by Autodave on 2021-06-27
My Win10 takes a little over a minute and my Xubuntu takes 22 seconds.  They are each on their own SSD and the Win10 is a faster SSD.  Most apps open withing a second or two on Linux, nowhere near that quickly in Windows.  Also, my Win10 is very stripped down since I only play one game on it.  No AV running or any not needed junk.

---

### Post by TheFu on 2021-06-27
Pick your software to match the capabilities of your hardware.
If you do that, then this is possible for a desktop:
```
$ systemd-analyze 
Startup finished in 2.842s (kernel) + 6.819s (userspace) = 9.662s 
graphical.target reached after 6.782s in userspace
```

But if you really want fast, just put the system into standby. That will be faster than booting.

Here's a virtual machine server with a lite-GUI:
```
$ systemd-analyze
Startup finished in 9.292s (kernel) + 14.067s (userspace) = 23.360s
graphical.target reached after 14.057s in userspace

```

Here's a Celeron system with over 32TB of storage connected.
```
$ systemd-analyze
Startup finished in 17.241s (kernel) + 1min 28.839s (userspace) = 1min 46.080s
graphical.target reached after 1min 28.822s in userspace
```
See how it takes much longer when there is more hardware connected?

OTOH, I don't really reboot these systems all that often. Taking 1.5 minutes every 2-3 weeks to reboot after a new kernel is installed doesn't bother me. I rebooted nearly all the systems yesterday, but have a few that weren't rebooted yet:
```
$ uptime
 22:21:18 up **22 days**, 12:56,  2 users,  load average: 0.07, 0.07, 0.01

```
and
```
$ uptime 
 22:22:05 up 5 days,  2:56,  4 users,  load average: 0.49, 0.29, 0.16
```
Here's a media player raspberry pi:
```
$ uptime
 22:22:40 up **43 days**,  8:07,  1 user,  load average: 0.21, 0.17, 0.11

```
So, how important is an extra minute at boot really?  To me, not at all, but we each have different needs.

---

### Post by pantazi on 2021-06-28
I use a ten year old HP 8460p, 2nd gen i5 and ssd and my results are:

```

~$ systemd-analyze 
Startup finished in 3.827s (kernel) + 10.094s (userspace) = 13.921s 
graphical.target reached after 10.081s in userspace 
```

---

### Post by ajgreeny on 2021-06-28
You haven't mentioned any hardware specs so it's difficult to say much more than has already been  said.
However, show us the output of command
***inxi -Fzx***
in terminal and it might help us to speed up your system if it's possible to do so.

---

### Post by Impavidus on 2021-06-28
Which Windows version compared to which Ubuntu version? Typically, Windows is slower than the Ubuntu version released in the same year. Windows has a pretty slow release cycle. The latest Windows is Windows 10, released about 6 years ago. Ubuntu versions that old are no longer supported. So the speed gap between them has been closing. When Windows 11 gets released later this year, I expect the speed gap to get larger again. Newer versions tend to be slower, for all operating systems.

---

### Post by josefranw on 2021-06-28
```
System:
  Kernel: 5.11.0-22-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 
  Desktop: GNOME 3.38.4 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Laptop System: Sony product: VGN-CS140F v: C102SHHD serial: <filter> 
  Mobo: Sony model: VAIO serial: <filter> BIOS: INSYDE v: R0260Q2 
  date: 09/19/2008 
Battery:
  ID-1: BAT1 charge: 36.8 Wh condition: 36.8/50.6 Wh (73%) 
  model: Sony Corp. VGP-BPS13 status: Full 
CPU:
  Info: Dual Core model: Intel Pentium Dual T3200 bits: 64 type: MCP 
  arch: Core Merom rev: D L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 7979 
  Speed: 997 MHz min/max: 1000/2000 MHz Core speeds (MHz): 1: 997 2: 997 
Graphics:
  Device-1: Intel Mobile 4 Series Integrated Graphics vendor: Sony 
  driver: i915 v: kernel bus ID: 00:02.0 
  Device-2: Ricoh Sony Visual Communication Camera Integrated Webcam 
  type: USB driver: uvcvideo bus ID: 1-2:2 
  Display: wayland server: X.Org 1.21.1.1 compositor: gnome-shell driver: 
  loaded: modesetting unloaded: fbdev,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express (CTG) 
  v: 2.1 Mesa 21.0.1 direct render: Yes 
Audio:
  Device-1: Intel 82801I HD Audio vendor: Sony driver: snd_hda_intel 
  v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.11.0-22-generic 
Network:
  Device-1: Marvell 88E8040 PCI-E Fast Ethernet vendor: Sony driver: sky2 
  v: 1.30 port: 4000 bus ID: 02:00.0 
  IF: enp2s0 state: down mac: <filter> 
  Device-2: Qualcomm Atheros AR928X Wireless Network Adapter vendor: Foxconn 
  driver: ath9k v: kernel port: 4000 bus ID: 03:00.0 
  IF: wlp3s0 state: down mac: <filter> 
  IF-ID-1: bnep0 state: unknown speed: N/A duplex: N/A mac: <filter> 
Bluetooth:
  Device-1: Alps BCM2046 Bluetooth Device type: USB driver: btusb v: 0.8 
  bus ID: 7-1:2 
  Report: ID: hci0 state: up running pscan iscan bt-v: 1.2 lmp-v: 2.1 
  address: <filter> 
Drives:
  Local Storage: total: 298.09 GiB used: 51.29 GiB (17.2%) 
  ID-1: /dev/sda vendor: Samsung model: HM321HI size: 298.09 GiB temp: 38 C 
Partition:
  ID-1: / size: 162.69 GiB used: 51.29 GiB (31.5%) fs: ext4 dev: /dev/sda5 
  ID-2: /boot/efi size: 512 MiB used: 12 KiB (0.0%) fs: vfat dev: /dev/sda3 
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 175.3 MiB (8.6%) file: /swapfile 
Sensors:
  System Temperatures: cpu: 50.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 258 Uptime: 5h 15m Memory: 2.79 GiB used: 1.82 GiB (65.4%) 
  Init: systemd runlevel: 5 Compilers: gcc: 10.3.0 Packages: 2269 
  Shell: Bash v: 5.1.4 inxi: 3.3.01
```

---

### Post by josefranw on 2021-06-28
```
systemd-analyzeStartup finished in 6.319s (kernel) + 2min 5.844s (userspace) = 2min 12.164s 
graphical.target reached after 2min 5.792s in userspace

```

---

### Post by tea for one on 2021-06-28
```
Machine:
  Type: Laptop System: Sony product: VGN-CS140F v: C102SHHD serial: <filter> 
  Mobo: Sony model: VAIO serial: <filter> BIOS: INSYDE v: R0260Q2 
  date: 09/19/2008 
```

A device from 2008 running a modern distro
```
Kernel: 5.11.0-22-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 
  Desktop: GNOME 3.38.4 Distro: Ubuntu 21.04 (Hirsute Hippo) 
```

It's not really surprising that it is a bit sluggish.

---

### Post by him610 on 2021-06-28
Here is someone's law on operating systems and applications, I guess it can be referred to as *SLoOSaA*
> All software expands to consume available resources.

---

### Post by TheFu on 2021-06-28
> **josefranw said:**
> ```
systemd-analyzeStartup finished in 6.319s (kernel) + 2min 5.844s (userspace) = 2min 12.164s 
graphical.target reached after 2min 5.792s in userspace

```

So .... a low-powered, 10 yr old, 3GB RAM system trying to run the high-end, Gnome3, latest Ubuntu is slow?  That doesn't surprise me.  I think that OS is slow on a Ryzen 5 2600! with 32GB of RAM!

```
System:
  Kernel: 5.11.0-22-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 
  Desktop: GNOME 3.38.4 Distro: Ubuntu 21.04 (Hirsute Hippo) 

```

The CPU has a passmark of 625.  Pretty much any chromebook ever made is faster. 
[https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+T3200+%40+2.00GHz&id=1143](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+T3200+%40+2.00GHz&id=1143)

Use xubuntu or lubuntu if you want any hope of performance.  On a system like that, I'd probably avoid using any Ubuntu and go with TinyCore instead.
Is this a laptop? If it is a desktop, for $20-$30 I'd buy a used CPU and 2x the RAM could be installed.  Or spend $75 and get a 2013 Chromebook with much more power, RAM, battery, and better video support.

---

### Post by ajgreeny on 2021-06-29
And what applications were running when you used that inxi command; using 1.89G of ram is quite high, depending on what was in use at the time.

However, TheFu is correct; you chose the wrong DE version to install for your hardware. See if things run smoother and faster using Lubuntu or Xubuntu.

---

### Post by yancek on 2021-06-29
I'd be curious to know what version of windows the OP is using as I don't see it mentioned in any posts.  I expect something like XP or vista which would make sense that an OS preinstalled on the cocmputer runs faster than a current OS.  Be interesting to see what would happen with windows 10 on that machine.

My experience has been similar to others that various Linux systems boot faster than windows 7 or 10 on recent machines.  Updating the BIOS firmware should increase the boot speed but I agree with others that Ubuntu is too heavy and a lighter system needs to be used.

---

### Post by josefranw on 2021-06-29
> **ajgreeny said:**
> And what applications were running when you used that inxi command; using 1.89G of ram is quite high, depending on what was in use at the time.

Just chrome.

---

### Post by josefranw on 2021-06-29
> **yancek said:**
> I'd be curious to know what version of windows the OP is using as I don't see it mentioned in any posts.
Windows 10

---

### Post by Autodave on 2021-06-29
Try Xubuntu: you will boot a lot quicker and everything will run quicker.  An SSD would help your situation a lot.

---

### Post by josefranw on 2021-06-29
I will try Xubuntu. Thanks for your help and support. Unfortunately, I can't just buy a new laptop or even a SSD.

---

### Post by TheFu on 2021-06-29
> **Autodave said:**
> Try Xubuntu: you will boot a lot quicker and everything will run quicker.  An SSD would help your situation a lot.

Excellent point.  Plus, a 2.5in SATA SSD, which would be compatible with almost any laptop from that time, could be moved to another machine later, provided it also supports 2.5in SATA HDDs.  

A new SSD would be the #2 performance boosting solution, after switching to a more appropriate DE (xfce or LXQt). Next would be a newer CPU with a better iGPU which will make video playback possible. Since 2010, the iGPUs on most intel CPUs has really changed the ability to view videos thanks to built-in mpeg2 and h.264 video decoders in the hardware.  Chromebooks all come with this newer hardware.

---

