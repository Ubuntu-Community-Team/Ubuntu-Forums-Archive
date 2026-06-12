---
title: "Ubuntu 14.04.2 4.13 Kernel No WiFi"
date: 2015-07-30
forum: General Help
---

### Post by Redalien0304 on 2015-07-30
upgraded Ubuntu 14.04.2 3.16.31 Kernel to 4.1.3 kernel after that no WiFi. On Dell Latitude E6400. did this from Page 1 here [http://ubuntuforums.org/showthread.php?t=2080753&page=2](http://ubuntuforums.org/showthread.php?t=2080753&page=2) i get this 
craig@craig-Latitude-E6400:~$ sudo apt-get install --reinstall bcmwl-kernel-sourceReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1,512 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/restricted bcmwl-kernel-source amd64 6.30.223.248+bdcom-0ubuntu0.1 [1,512 kB]
Fetched 1,512 kB in 19s (78.2 kB/s)                                            
(Reading database ... 407175 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.1_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.1) over (6.30.223.248+bdcom-0ubuntu0.1) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.1) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 4.1.3-040103-generic
Building for architecture x86_64
Building initial module for 4.1.3-040103-generic
ERROR (dkms apport): kernel package linux-headers-4.1.3-040103-generic is not supported
Error! Bad return status for module build on kernel: 4.1.3-040103-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-4.1.3-040103-generic
craig@craig-Latitude-E6400:~$ sudo modprobe wl
modprobe: FATAL: Module wl not found.

I did get a USB ETECITY Wifi going but want onboard Wifi working.

Any help is Much Appreciated Thanks

---

### Post by QDR06VV9 on 2015-07-30
See if this gets you up.
```
[COLOR=#000000]sudo add-apt-repository ppa:longsleep/bcmwl
sudo apt-get update
sudo apt-get install bcmwl-kernel-source[/COLOR]
```

```
me@me-Lenovo-B570:~$ inxi -Fxz
System:    Host: me-Lenovo-B570[COLOR=#006400] Kernel: 4.1.3-040103-generic x86_64[/COLOR] (64 bit, gcc: 4.8.4) 
           Desktop: N/A Distro: Ubuntu 14.04 trusty
Machine:   System: LENOVO product: 1068AJU version: Lenovo B570
           Mobo: LENOVO model: Emerald Lake version: FAB1 Bios: LENOVO version: 44CN43WW date: 10/27/2011
CPU:       Dual core Intel Pentium CPU B950 (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3) bmips: 8381.12 
           Clock Speeds: 1: 1609.863 MHz 2: 1839.632 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile GLX Version: 3.0 Mesa 10.6.3 Direct Rendering: Yes
Audio:     Card: Intel 6 Series/C200 Series Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Sound: Advanced Linux Sound Architecture ver: k4.1.3-040103-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: 2000 bus-ID: 03:00.0
           IF: eth0 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) driver: ath9k bus-ID: 02:00.0
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (29.0% used) 1: id: /dev/sda model: TOSHIBA_MK5065GS size: 500.1GB 
Partition: ID: / size: 454G used: 135G (32%) fs: ext4 ID: /boot size: 237M used: 135M (61%) fs: ext2 
           ID: swap-1 size: 4.20GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 55.0C mobo: 40.0C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 199 Uptime: 4 min Memory: 438.1/3865.8MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 
```
Kind Regards

---

### Post by Redalien0304 on 2015-07-31
Thanks Worked Perfectly. no problems. Thanks runrickus :p

---

