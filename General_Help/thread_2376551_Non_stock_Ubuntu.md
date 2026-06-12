---
title: "Non stock Ubuntu"
date: 2017-11-03
forum: General Help
---

### Post by meetdilip on 2017-11-03
I was using stock 12.04 > upgraded to 14.04 > tried a couple of other DE ( Cinnmaon, Gnome ) > automatically lost Unity while in Cinnamon > Upgraded to 16.04 ( with some help )

@vasa1 told me that my Ubuntu 16.04 is not stock. He might be correct. Because I tried other desktop and that might have made changes to my PC. I have removed other DE and upgraded to 16.04. Everything works fine. I would like to clean the mess and use stock Unity. I don't want to do a fresh install. Is it possible to revert packages to stock Ubuntu 16.04 ? 

A quick look at my PC

> $ inxi -Fxz
System: Host: my-PC Kernel: 4.4.0-98-generic x86_64 (64 bit gcc: 5.4.0)
Desktop: Unity 7.4.0 (Gtk 3.20.8-1ubuntu0~ppa1)
Distro: Ubuntu 16.04 xenial
Machine: System: Dell (portable) product: Vostro 3550
Mobo: Dell model: 0PD77K v: A12 Bios: Dell v: A12 date: 02/18/2014
CPU: Dual core Intel Core i5-2430M (-HT-MCP-) cache: 3072 KB
flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9578
clock speeds: max: 3000 MHz 1: 897 MHz 2: 883 MHz 3: 811 MHz
4: 804 MHz
Graphics: Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
bus-ID: 00:02.0
Card-2: Advanced Micro Devices [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M]
bus-ID: 01:00.0
Display Server: X.Org 1.18.4 drivers: ati,radeon,intel (unloaded: fbdev,vesa)
Resolution: 1366x768@60.00hz
GLX Renderer: Mesa DRI Intel Sandybridge Mobile
GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
Audio: Card Intel 6 Series/C200 Series Family High Definition Audio Controller
driver: snd_hda_intel bus-ID: 00:1b.0
Sound: Advanced Linux Sound Architecture v: k4.4.0-98-generic
Network: Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 05:00.0
IF: eth0 state: down mac: <filter>
Card-2: Broadcom BCM4313 802.11bgn Wireless Network Adapter
driver: wl bus-ID: 09:00.0
IF: wlan0 state: up mac: <filter>
Drives: HDD Total Size: 500.1GB (56.5% used)
ID-1: /dev/sda model: ST500LT012 size: 500.1GB
Partition: ID-1: / size: 129G used: 79G (65%) fs: ext4 dev: /dev/sda6
ID-2: swap-1 size: 44.55GB used: 0.15GB (0%) fs: swap dev: /dev/sda5
RAID: No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors: System Temperatures: cpu: 57.0C mobo: N/A gpu: N/A
Fan Speeds (in rpm): cpu: N/A
Info: Processes: 259 Uptime: 42 min Memory: 2389.3/3857.3MB
Init: systemd runlevel: 5 Gcc sys: 5.4.0
Client: Shell (bash 4.3.481) inxi: 2.2.35

> $ apt policy nautilus
nautilus:
Installed: 1:3.20.3-1ubuntu2~ubuntu16.04.1
Candidate: 1:3.20.3-1ubuntu2~ubuntu16.04.1
Version table:
*** 1:3.20.3-1ubuntu2~ubuntu16.04.1 100
100 /var/lib/dpkg/status
1:3.18.4.is.3.14.3-0ubuntu6 500
500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
1:3.18.4.is.3.14.3-0ubuntu4 500
500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages

Thanks

---

### Post by vasa1 on 2017-11-03
You've also got GTK 3.20 while 16.04 is still on GTK 3.18.

---

### Post by meetdilip on 2017-11-03
Where can I look for non stock packages ? Is it possible to replace them ?

---

### Post by ian-weisser on 2017-11-03
Downgrading is possible, but it may be a real project. Definitely not a 10-minute, three-apt-command-then-go-get-a-sandwich break from your normal routine.

First, check your sources for PPAs and other non-Ubuntu repos. Disable them.
You got that Nautilus package from *somewhere*. It wasn't beamed in by aliens.

Then you must decide: Really downgrade and risk breakage...or simply wait six months and let 18.04 overwrite most of those non-Ubuntu packages.
Example: That non-Ubuntu nautilus 3.20 will be overwritten by 3.26 in 18.04.

 Apt always wants to install the higher version, regardless of source.

If you really want to downgrade, it sometimes gets scary: You uninstall ALL the non-Ubuntu packages. It might uninstall much of your Desktop Environment. Then you re-install the versions from the Ubuntu Repositories.

---

### Post by meetdilip on 2017-11-03
I see. If 18.04 upgrade can fix it, I am perfectly ok with it. The root of all this was Unity got lost automatically when I was using Cinnamon. Not sure what went wrong, and where. Thanks.

---

### Post by meetdilip on 2017-11-08
I added andtried** purge** the following PPAs one by one as per directions from @deadflowr

> sudo add-apt-repository ppa:gnome3-team/gnome3-staging

sudo add-apt-repository ppa:gnome3-team/gnome3 

As of now, I have the following

> $ inxi -Fxz
System: Host: dna-Vostro-3550 Kernel: 4.4.0-98-generic x86_64 (64 bit gcc: 5.4.0)
Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3)
Distro: Ubuntu 16.04 xenial
Machine: System: Dell (portable) product: Vostro 3550
Mobo: Dell model: 0PD77K v: A12 Bios: Dell v: A12 date: 02/18/2014
CPU: Dual core Intel Core i5-2430M (-HT-MCP-) cache: 3072 KB
flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9578
clock speeds: max: 3000 MHz 1: 856 MHz 2: 906 MHz 3: 853 MHz
4: 999 MHz
Graphics: Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
bus-ID: 00:02.0
Card-2: Advanced Micro Devices [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M]
bus-ID: 01:00.0
Display Server: X.Org 1.18.4 drivers: ati,radeon,intel (unloaded: fbdev,vesa)
Resolution: 1366x768@60.00hz
GLX Renderer: Mesa DRI Intel Sandybridge Mobile
GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
Audio: Card Intel 6 Series/C200 Series Family High Definition Audio Controller
driver: snd_hda_intel bus-ID: 00:1b.0
Sound: Advanced Linux Sound Architecture v: k4.4.0-98-generic
Network: Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 05:00.0
IF: eth0 state: down mac: <filter>
Card-2: Broadcom BCM4313 802.11bgn Wireless Network Adapter
driver: wl bus-ID: 09:00.0
IF: wlan0 state: up mac: <filter>
Drives: HDD Total Size: 500.1GB (52.8% used)
ID-1: /dev/sda model: ST500LT012 size: 500.1GB
Partition: ID-1: / size: 129G used: 78G (64%) fs: ext4 dev: /dev/sda6
ID-2: swap-1 size: 44.55GB used: 0.02GB (0%) fs: swap dev: /dev/sda5
RAID: No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors: System Temperatures: cpu: 57.0C mobo: N/A gpu: N/A
Fan Speeds (in rpm): cpu: N/A
Info: Processes: 253 Uptime: 32 min Memory: 2850.9/3857.3MB
Init: systemd runlevel: 5 Gcc sys: 5.4.0
Client: Shell (bash 4.3.481) inxi: 2.2.35 



> $ apt policy nautilus
nautilus:
Installed: 1:3.18.4.is.3.14.3-0ubuntu6
Candidate: 1:3.18.4.is.3.14.3-0ubuntu6
Version table:
*** 1:3.18.4.is.3.14.3-0ubuntu6 500
500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
100 /var/lib/dpkg/status
1:3.18.4.is.3.14.3-0ubuntu4 500
500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages



I could still see Gnome Flashback ( Metacity ) and Gnome Flashback ( Compiz ) through login options.

Update :

Got rid of Gnome Flashback entries with **purge**

---

