---
title: "Nomodeset/Black Screen Problem"
date: 2019-08-16
forum: General Help
---

### Post by dirtys2 on 2019-08-16
[COLOR=#121112][FONT=&quot]Hey, guys.. First of all, I've had a problem for a few days. My computer also has Windows 10 installed and I am trying to install Ubuntu OS along with that. Ubuntu OS, I'm running the setup and on the full Setup screen, the screen goes blank. No signal appears on the monitor but the problem is corrected when I press the monitor button and then turn it on / off. However, the screen darkens again temporarily after an average of 1 minute. Turns the screen on and off, even if I finish the installation when I log in normally does this. Apart from that, I have the same problem in all Linux OS. When running with N[/FONT][/COLOR]omodeset[COLOR=#121112][FONT=&quot] it works fine but the screen resolution is fixed at 800x600. Note; My CPU and GPU is AMD.[/FONT][/COLOR]

---

### Post by TheFu on 2019-08-16
When seeking help that is hardware related, always:

[LIST]
[*]Say which OS you are running - 18.04?  Different versions have different answers.
[*]Say which desktop you are using - Gnome3, Mate, LXQt, KDE, ....   Different DEs have different answers.
[*]Say the vendor and model of the PC/Laptop. Model numbers required. Good to google "ubuntu {vendor + model} issue"
[*]Say any specific models of GPUs, if it is a graphical/screen issue.
[/LIST]

Hard to help without those facts.  **inxi -Fz** will gather overview about a system. inxi isn't pre-installed. Just **sudo apt install inxi**

Often, the driver being used for the problem will be requested. For the GPU, **sudo lshw -C video** output will provide that data.  Please.

---

### Post by dirtys2 on 2019-08-17
> **TheFu said:**
> When seeking help that is hardware related, always:

[LIST]
[*]Say which OS you are running - 18.04?  Different versions have different answers. 
[*]Say which desktop you are using - Gnome3, Mate, LXQt, KDE, ....   Different DEs have different answers. 
[*]Say the vendor and model of the PC/Laptop. Model numbers required. Good to google "ubuntu {vendor + model} issue" 
[*]Say any specific models of GPUs, if it is a graphical/screen issue. 
[/LIST]

Hard to help without those facts.  **inxi -Fz** will gather overview about a system. inxi isn't pre-installed. Just **sudo apt install inxi**

Often, the driver being used for the problem will be requested. For the GPU, **sudo lshw -C video** output will provide that data.  Please.

Sure these about my system.

```
System:
  Host: ubuntu Kernel: 5.0.0-13-generic x86_64 bits: 64 
  Desktop: Gnome 3.32.0 Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:
  Type: Desktop System: Gigabyte product: N/A v: N/A serial: <filter> 
  Mobo: Gigabyte model: F2A68HM-DS2 v: x.x serial: <filter> 
  UEFI: American Megatrends v: FE date: 10/09/2018 
CPU:
  Topology: Quad Core model: AMD Athlon X4 860K bits: 64 type: MCP 
  L2 cache: 2048 KiB 
  Speed: 1696 MHz min/max: 1700/3700 MHz Core speeds (MHz): 1: 1696 2: 1695 
  3: 2053 4: 1807 
Graphics:
  Device-1: AMD Turks PRO [Radeon HD 6570/7570/8550] driver: radeon 
  v: kernel 
  Display: x11 server: X.Org 1.20.4 driver: radeon 
  resolution: 1920x1080~60Hz 
  Message: Unable to show advanced data. Required tool glxinfo missing. 
Audio:
  Device-1: AMD FCH Azalia driver: snd_hda_intel 
  Device-2: AMD Turks HDMI Audio [Radeon HD 6500/6600 / 6700M Series] 
  driver: snd_hda_intel 
  Device-3: Kingston type: USB driver: hid-generic,snd-usb-audio,usbhid 
  Sound Server: ALSA v: k5.0.0-13-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 938.98 GiB used: 2.46 GiB (0.3%) 
  ID-1: /dev/sda vendor: Seagate model: ST1000DM003-1CH162 size: 931.51 GiB 
  ID-2: /dev/sdb type: USB model: USB DISK 2.0 size: 7.46 GiB 
Partition:
  ID-1: / size: 3.90 GiB used: 514.3 MiB (12.9%) fs: overlay source: ERR-102 
Sensors:
  Missing: Required tool sensors not installed. Check --recommends 
Info:
  Processes: 201 Uptime: 19m Memory: 7.80 GiB used: 1.68 GiB (21.5%) 
  Shell: bash inxi: 3.0.36 


```

```
*-display                 
       description: VGA compatible controller
       product: Turks PRO [Radeon HD 6570/7570/8550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:35 memory:c0000000-cfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:c0000-dffff


```

---

### Post by TheFu on 2019-08-17
Thanks for the output.  If you don't want to, you don't need to include everything in the inxi.  But always include the full output AND the command run for lshw  output.  The command run is VERY important, so experts can know what should be there that might be missing.  It also helps the next person also trying to learn to solve their own issues.

 The relevant inxi lines for THIS issue are:```

System:
  Host: ubuntu Kernel: 5.0.0-13-generic x86_64 bits: 64 
  Desktop: **Gnome 3.32.0** Distro: **Ubuntu 19.04** (Disco Dingo) 
Machine:
  Type: Desktop System: Gigabyte product: N/A v: N/A serial: <filter> 
  Mobo: **Gigabyte** model: **F2A68HM-DS2** v: x.x serial: <filter> 
  UEFI: American Megatrends v: FE date: 10/09/2018 
CPU:
  Topology: Quad Core model: AMD **Athlon X4 860K** bits: 64 type: MCP 
Graphics:
  Device-1: AMD Turks PRO [**Radeon HD 6570/7570/8550**] driver: **radeon**  v: **kernel** 
  Display: **x11** server: X.Org 1.20.4 driver: **radeon** 
  resolution: **1920x1080~60Hz** 
  Message: Unable to show advanced data. **Required tool glxinfo missing**. 
```

My google of "*ubuntu 19.04  Radeon HD 6570/7570/8550*" found:
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)   Don't know what good that is, but it is the PPA I see recommended to get the latest F/LOSS drivers for that card. 19.04 is listed as "supported."  I really wish the specific version of the Radeon driver were listed.

Run:
```
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt update
sudo apt upgrade
reboot
```
That should update the drivers and keep them current.  When you move to 19.10 in November, that repo will be disabled by the release upgrade process, so you'll need to do this again. Support for 19.04 ends this January.  I only use LTS releases to avoid the 6-month mandatory upgrade cycle.
PPAs integrate outside repositories into your system's package management tools.  This capability is one of the main reasons I prefer Ubuntu over other OS options.

BTW, if it were a laptop, the model would really help in a google search for solving the issue. Not so much help with this issue, but sometimes it is extremely helpful. ;)

I have no idea whether those new drivers will help or not.  If they don't, you can remove the PPA, do an update/upgrade cycle and reboot to be back where you are now.

---

### Post by dirtys2 on 2019-08-17
First one, thank you. I did what you text it step to step but doesn't work it. My problem still going to same.

---

### Post by Autodave on 2019-08-17
If that machine were mine, I would try downloading 18.04 and booting from that to see if my graphics would work properly. If so, then I would install 18.04 and be done with it for a little while.

---

### Post by dirtys2 on 2019-08-17
I will try. I guess, will not work because I got some problem on every Linux OS.

---

### Post by TheFu on 2019-08-17
Drivers for LTS versions, like 18.04, are maintained better with both nvidia and amd making it possible for Canonical to install the proprietary drivers fairly easily for supported GPUs.  Just last month, nvidia enabled this for 18.04 and 16.04 releases.  

Might check the motherboard BIOS for power saving modes. If you have another PC, you can setup ssh-server on the Ubuntu one and ssh into it from another device, then watch the logs as the screen blanks.  Something should show up in the log files which might trace the issue.  Logs are in /var/log/ .... there are a bunch, so I'd look at them based on modification time when you see the blank happen.

---

### Post by dirtys2 on 2019-08-17
I got no another PC.

---

### Post by TheFu on 2019-08-17
> **dirtys2 said:**
> I got no another PC.

Phone? Tablet? on the same LAN?  Every networked OS has an ssh client.

---

### Post by dirtys2 on 2019-08-18
> **TheFu said:**
> Phone? Tablet? on the same LAN?  Every networked OS has an ssh client.

I got only one Iphone 4.

---

### Post by dirtys2 on 2019-08-18
> **TheFu said:**
> Phone? Tablet? on the same LAN?  Every networked OS has an ssh client.
Can I change screen resolution while booting with nomodeset?

---

