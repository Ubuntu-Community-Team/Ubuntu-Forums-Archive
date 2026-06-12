---
title: "ALSA Files Missing from Newer Kernels"
date: 2022-08-13
forum: General Help
---

### Post by Fuzzy-Mark on 2022-08-13
I was told the reason why my Digigram VX882e sound card will not work is because some ALSA files were removed from the newer kernels. I'm using Linux Mint 20.3 with kernel 5.4.0-122. I either need to know when they were removed so I can load an older version of Linux Mint that has a kernel that supports ALSA or if there is a way to add the missing files back to the newer kernel and how to do it.

Which kernel version is the newest before ALSA files were removed?

Thanks

```

ocean@SuperLogics:~$  inxi -FAxz
System:
  Kernel: 5.4.0-122-generic x86_64 bits: 64 compiler: gcc v: 9.4.0 
  Desktop: MATE 1.26.0 Distro: Linux Mint 20.3 Una base: Ubuntu 20.04 focal 
Machine:
  Type: Desktop Mobo: ASRock model: H370 Pro4 serial: <filter> 
  UEFI [Legacy]: American Megatrends v: P1.00 date: 02/09/2018 
CPU:
  Topology: 6-Core model: Intel Core i5-8600K bits: 64 type: MCP 
  arch: Kaby Lake rev: A L2 cache: 9216 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 43200 
  Speed: 4250 MHz min/max: 800/4300 MHz Core speeds (MHz): 1: 4250 2: 3896 
  3: 3585 4: 4216 5: 4235 6: 4227 
Graphics:
  Device-1: Intel UHD Graphics 630 vendor: ASRock driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.13 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1360x768~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2) v: 4.6 Mesa 21.2.6 
  direct render: Yes 
Audio:
  Device-1: PLX PCI9056 32-bit 66MHz PCI <-> IOBus Bridge vendor: Digigram 
  driver: N/A bus ID: 02:04.0 
  Sound Server: ALSA v: k5.4.0-122-generic 
Network:
  Device-1: Intel Ethernet I219-V vendor: ASRock driver: e1000e v: 3.2.6-k 
  port: efa0 bus ID: 00:1f.6 
  IF: eno1 state: up speed: 100 Mbps duplex: full mac: <filter> 
  Device-2: Intel 82574L Gigabit Network driver: e1000e v: 3.2.6-k 
  port: 7000 bus ID: 04:00.0 
  IF: enp4s0 state: down mac: <filter> 
  Device-3: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 6000 bus ID: 07:00.0 
  IF: enp7s0 state: down mac: <filter> 
  Device-4: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 5000 bus ID: 08:00.0 
  IF: enp8s0 state: down mac: <filter> 
  Device-5: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 4000 bus ID: 09:00.0 
  IF: enp9s0 state: down mac: <filter> 
  Device-6: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 3000 bus ID: 0a:00.0 
  IF-ID-1: enp10s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 7.73 TiB used: 14.12 GiB (0.2%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 960 EVO 500GB 
  size: 465.76 GiB 
  ID-2: /dev/sda vendor: HGST (Hitachi) model: HUH728080ALE600 
  size: 7.28 TiB 
Partition:
  ID-1: / size: 456.88 GiB used: 14.12 GiB (3.1%) fs: ext4 
  dev: /dev/nvme0n1p5 
Sensors:
  System Temperatures: cpu: 52.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 214 Uptime: 12m Memory: 31.04 GiB used: 1.29 GiB (4.2%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38
```

P.S. I posted a question about my sound card in the Hardware forum but I found out the reason it doesn't work is because the ALSA files were removed.

---

### Post by Doug S on 2022-08-14
Do you have the alsa-firmware-loaders package installed? If not you might need it, not sure, but it lists /usr/bin/vxloader and usr/share/doc/alsa-firmware-loaders/vxloader/README in its contents.

---

### Post by Fuzzy-Mark on 2022-08-14
Thanks, I installed that package and fxload was also installed but sound card still not recognized. It lists some packages that were automatically installed and are no longer required. Should I remove them?

I did find the files in usr/bin and usr/share/doc and it looks like vxloader has a driver for the VX222 sound card but I didn't see one for VX882e. Is it maybe the same driver?

inxi -Fxz lists the sound card driver as N/A.  How do I assign the driver?

Thanks.

```
ocean@SuperLogics:~$ sudo apt install alsa-firmware-loaders[sudo] password for ocean:        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:

  linux-headers-5.4.0-121 linux-headers-5.4.0-121-generic
  linux-headers-5.4.0-122 linux-headers-5.4.0-122-generic
  linux-image-5.4.0-121-generic linux-image-5.4.0-122-generic

  linux-modules-5.4.0-121-generic linux-modules-5.4.0-122-generic

  linux-modules-extra-5.4.0-121-generic linux-modules-extra-5.4.0-122-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  fxload
The following NEW packages will be installed:
  alsa-firmware-loaders fxload
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.6 kB of archives.
After this operation, 253 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/universe amd64 fxload amd64 0.0.20081013-1ubuntu2 [15.6 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/multiverse amd64 alsa-firmware-loaders amd64 1.1.7-1ubuntu1 [25.0 kB]

Fetched 40.6 kB in 1s (30.3 kB/s)                

Selecting previously unselected package fxload.
(Reading database ... 502175 files and directories currently installed.)

Preparing to unpack .../fxload_0.0.20081013-1ubuntu2_amd64.deb ...

Unpacking fxload (0.0.20081013-1ubuntu2) ...
Selecting previously unselected package alsa-firmware-loaders.
Preparing to unpack .../alsa-firmware-loaders_1.1.7-1ubuntu1_amd64.deb ...
Unpacking alsa-firmware-loaders (1.1.7-1ubuntu1) ...
Setting up fxload (0.0.20081013-1ubuntu2) ...
Setting up alsa-firmware-loaders (1.1.7-1ubuntu1) ...

Processing triggers for man-db (2.9.1-1) ...

ocean@SuperLogics:~$ alsamixer

cannot open mixer: No such file or directory
```

```
ocean@SuperLogics:~$ inxi -FxzSystem:
  Kernel: 5.15.0-46-generic x86_64 bits: 64 compiler: N/A 
  Desktop: MATE 1.26.0 Distro: Linux Mint 20.3 Una base: Ubuntu 20.04 focal 
Machine:
  Type: Desktop Mobo: ASRock model: H370 Pro4 serial: <filter> 
  UEFI [Legacy]: American Megatrends v: P1.00 date: 02/09/2018 
CPU:
  Topology: 6-Core model: Intel Core i5-8600K bits: 64 type: MCP 
  arch: Kaby Lake rev: A L2 cache: 9216 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 43200 
  Speed: 4184 MHz min/max: 800/4300 MHz Core speeds (MHz): 1: 4184 2: 4164 
  3: 4185 4: 4177 5: 4185 6: 4268 
Graphics:
  Device-1: Intel UHD Graphics 630 vendor: ASRock driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: [X.Org]("http://X.Org") 1.20.13 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1360x768~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2) v: 4.6 Mesa 21.2.6 
  direct render: Yes 
Audio:
  Device-1: PLX PCI9056 32-bit 66MHz PCI <-> IOBus Bridge vendor: Digigram 
  driver: N/A bus ID: 02:04.0 
  Sound Server: ALSA v: k5.15.0-46-generic 
Network:
  Device-1: Intel Ethernet I219-V vendor: ASRock driver: e1000e v: kernel 
  port: efa0 bus ID: 00:1f.6 
  IF: eno1 state: down mac: <filter> 
  Device-2: Intel 82574L Gigabit Network driver: e1000e v: kernel port: 7000 
  bus ID: 04:00.0 
  IF: enp4s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
  Device-3: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 6000 bus ID: 07:00.0 
  IF: enp7s0 state: down mac: <filter> 
  Device-4: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 5000 bus ID: 08:00.0 
  IF: enp8s0 state: down mac: <filter> 
  Device-5: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 4000 bus ID: 09:00.0 
  IF: enp9s0 state: down mac: <filter> 
  Device-6: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 3000 bus ID: 0a:00.0 
  IF-ID-1: enp10s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 7.73 TiB used: 69.08 GiB (0.9%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 960 EVO 500GB 
  size: 465.76 GiB 
  ID-2: /dev/sda vendor: HGST (Hitachi) model: HUH728080ALE600 
  size: 7.28 TiB 
Partition:
  ID-1: / size: 456.88 GiB used: 69.08 GiB (15.1%) fs: ext4 
  dev: /dev/nvme0n1p5 
Sensors:
  System Temperatures: cpu: 49.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 200 Uptime: 11m Memory: 31.04 GiB used: 658.9 MiB (2.1%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38


```


[FONT=Arial]
 [/FONT]

---

### Post by Fuzzy-Mark on 2022-08-14
This is in the README file in vxloader:

```
    VXLOADER - Firmware loader for Digigram VX soundcards
        Takashi Iwai <tiwai@suse.de>


GENERAL
=======

Vxloader is a helper program to load the firmware binaries
onto the Digigram's VX-board sound drivers.
The following modules require this program:
    snd-vx222, snd-vxpocket, snd-vxp440
These drivers don't work properly at all until the certain firmwares
are loaded, i.e. no PCM nor mixer devices will appear.


USAGE
=====

When vxloader is invoked without options, it will probe all existing
soundcards until a valid VX-driver is found.  If a valid VX-driver is
found, vxloader reads the board type from the driver.  The corresponding
firmware binaries are then read and transferred to the driver.
Finally, vxloader initializes the PCM and the mixer devices on the
driver for making the soundcard full functional.

Instead of auto-probing, you can specify the card number or the hwdep
device name via -c and -D options, respectively.

    % vxloader -c 1
    % vxloader -D hw:0

For loading the firmware automatically after the module is loaded, use
the post-install command.  For example, add the following entry to
/etc/modules.conf for VX222 driver:

    post-install snd-vx222 /usr/bin/vxloader

FILES
=====

The firmware binaries are installed on /usr/share/alsa/firmware/vxloader
(or /usr/local/share/alsa/firmware/vxloader, depending to the prefix
option of configure).  There will be *.conf files, which define the dsp
image files for each different card type.


COPYRIGHT
=========

Copyright (c) 2003 Takashi Iwai <tiwai@suse.de>
Distributable under GPL.

The firmware files included in alsa-firmware package are copyright
by Digigram S.A.
```

---

### Post by Doug S on 2022-08-14
I don't know if I can help further. I am a server person, and don't know about linux sound. There is a "vx" directory in the linux source tree:

```
doug@s19:~/kernel/linux$ ls -l sound/drivers/vx
total 112
-rw-rw-r-- 1 doug doug   242 Oct 19  2019 Makefile
-rw-rw-r-- 1 doug doug  4507 May  8  2021 vx_cmd.c
-rw-rw-r-- 1 doug doug  7297 Oct 19  2019 vx_cmd.h
-rw-rw-r-- 1 doug doug 20150 Oct 31  2021 vx_core.c
-rw-rw-r-- 1 doug doug  2629 Oct 31  2021 vx_hwdep.c
-rw-rw-r-- 1 doug doug 28224 Oct 31  2021 vx_mixer.c
-rw-rw-r-- 1 doug doug 32350 Oct 31  2021 vx_pcm.c
-rw-rw-r-- 1 doug doug  6954 Oct 19  2019 vx_uer.c
```
and the most recentt commit seems to be from 2021:
```

doug@s19:~/kernel/linux$ git log --oneline sound/drivers/vx | head -1
a033954140ac ALSA: vx: Manage vx_core object with devres
doug@s19:~/kernel/linux$ git show a033954140ac
commit a033954140ac43a8ce0eab469229a107cfee1c87
Author: Takashi Iwai <tiwai@suse.de>
Date:   [COLOR="#FF0000"]Thu Jul 15 09:59:11 2021[/COLOR] +0200

    ALSA: vx: Manage vx_core object with devres

    The firmware data are also released automatically.

    Link: https://lore.kernel.org/r/20210715075941.23332-50-tiwai@suse.de
    Signed-off-by: Takashi Iwai <tiwai@suse.de>

diff --git a/sound/drivers/vx/vx_core.c b/sound/drivers/vx/vx_core.c
index a10449af5a76..18901e5bcfcf 100644

```One might have to compile themselves, using the Makefile, but I don't know for certain.

There is also this in the kernel source tree:

```
doug@s19:~/kernel/linux$ ls -l sound/pci/vx222
total 52
-rw-rw-r-- 1 doug doug   200 Oct 19  2019 Makefile
-rw-rw-r-- 1 doug doug  5611 Oct 31  2021 vx222.c
-rw-rw-r-- 1 doug doug  3690 May  8  2021 vx222.h
-rw-rw-r-- 1 doug doug 34979 Oct 31  2021 vx222_ops.c
```

EDIT: I found this, but am not sure of the relevance:

```

doug@s19:~/kernel/linux/[COLOR="#FF0000"]sound/pci/pcxhr[/COLOR]$ grep -i 882E *
pcxhr.c:        PCI_ID_VX882E,
pcxhr.c:        PCI_ID_PCX882E,
pcxhr.c:        { 0x10b5, 0x9056, 0x1369, 0xb021, 0, 0, PCI_ID_[COLOR="#FF0000"]VX882E[/COLOR], },
pcxhr.c:        { 0x10b5, 0x9056, 0x1369, 0xb121, 0, 0, PCI_ID_PCX882E, },
pcxhr.c:[PCI_ID_VX882E] =       { "[COLOR="#FF0000"]VX882e[/COLOR]",       4, 4, 1, 41 },
pcxhr.c:[PCI_ID_PCX882E] =      { "PCX882e",      4, 4, 1, 41 },
pcxhr_hwdep.c:  [1] = { "xlxint.dat", "xlxc882e.dat",
pcxhr_hwdep.c:          "dspe882.e56", "dspb882e.b56", "dspd882.d56" },
pcxhr_hwdep.c:MODULE_FIRMWARE("pcxhr/xlxc882e.dat");
pcxhr_hwdep.c:MODULE_FIRMWARE("pcxhr/dspb882e.b56");

```
and```

doug@s19:~/kernel/linux$ [COLOR="#FF0000"]head sound/pci/pcxhr/pcxhr.c[/COLOR]
// SPDX-License-Identifier: GPL-2.0-or-later
/*
 * Driver for Digigram pcxhr compatible soundcards
 *
 * main file with alsa callbacks
 *
 * Copyright (c) 2004 by Digigram <alsa@digigram.com>
 */

```
Is that module, file name: snd-pcxhr.ko,  loaded? If not does it help to force load it? Not certain of the module name, try snd-pcxhr

---

### Post by Fuzzy-Mark on 2022-08-14
Thanks, I'll try that

---

### Post by Doug S on 2022-08-14
I think you might also need the file name snd-vx-lib.ko module, but again I am not sure of the name maybe "snd-vx-lib-objs" or just "snd-vx-lib".

As far as I can determine, all of this stuff is compiled as modules with the default Ubuntu kernel configuration so it should just be a matter of something figuring out that the modules are needed and to load them.

---

### Post by Fuzzy-Mark on 2022-08-19
Once I figured out how to load a module, I tried that and it seems to have worked.

```
sudo modprobe snd-pcxhr
```

I haven't tried all the channels but it seems channel 1 and 2 outputs  are working for standard stereo output and the card shows up three times in aplay -l. I only have one XLR cable at the  moment so I'll continue testing later.

Thank you so much for your advice

---

### Post by Fuzzy-Mark on 2022-08-24
I reinstalled my OS and upgraded to Mint 20.4 and that command was not enough.

I had to do all of the following to get it to work:
```
 sudo apt install alsa-tools 
```
```
 sudo apt install alsa-firmware-loaders 
```

I downloaded the ALSA firmware from [https://www.alsa-project.org/files/pub/firmware/alsa-firmware-1.2.4.tar.bz2](https://www.alsa-project.org/files/pub/firmware/alsa-firmware-1.2.4.tar.bz2) and extracted to my home folder, then:

```
 sudo apt install build-essential 
```
Change directory to extracted folder:
```
 cd ~/(name of extracted folder) 
``` mine was called "alsa-firmware-1.2.4"
```
 ./configure 
```
```
 make 
```
```
 sudo make install 
```
```
 sudo modprobe snd-pcxhr 
```

Then rebooted and it works.

I followed this thread for the ALSA firmware install [https://askubuntu.com/questions/493122/digigram-vx222hr-not-detected](https://askubuntu.com/questions/493122/digigram-vx222hr-not-detected)

---

