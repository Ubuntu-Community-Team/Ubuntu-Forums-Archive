---
title: "Horrible memory management in Bionic"
date: 2018-05-20
forum: General Help
---

### Post by GoCool on 2018-05-20
I have an Alienware with around 16GB of Ram. I installed Kubuntu 18.04. Now for half an hour I am waiting for my machine to respond so that I can take some log files and post it here.
I have my class playing right now...and i can't pause it, close it or do any thing ... my mouse cursor is the only thing which moves and a frozen screen. 
The following background applications are running
1. VLC player 
2. Mozilla firefox
3. Google chrome
4. R Studio
5. Dolphin File browser
6. evince pdf reader

Does anyone else have this issue?

I had my virtual machine open before but I closed it, not sure if Bionic was able to release the memory blocked by it.

---

### Post by ajgreeny on 2018-05-20
What does the command ```
top
``` in terminal tell you is using all your memory; are you certain it really is memory that is the limiting resource?

What is your hardware?
Run commands ```
inxi -F
free -m
``` one by one in terminal and report back here what the output is.

---

### Post by GoCool on 2018-05-20
I am not sure how this is going to help as I had to do a hard boot of the machine to get to a state where I can start using.
So here's the output after reboot.

top
[IMG]https://farm1.staticflickr.com/961/42244639791_cff06a7ec1_z.jpg[/IMG]

```
top - 22:00:43 up  7:12,  3 users,  load average: 0.10, 0.26, 0.31
Tasks: 345 total,   1 running, 259 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.3 us,  0.3 sy,  0.0 ni, 98.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 16308048 total,  6507812 free,  5192828 used,  4607408 buff/cache
KiB Swap: 16658428 total, 16658428 free,        0 used. 10388772 avail Mem 


```

inxi -F

```
gokul@gokul-Alienware-17:~/Desktop$ inxi -F
System:    Host: gokul-Alienware-17 Kernel: 4.15.0-20-generic x86_64 bits: 64 Desktop: KDE Plasma 5.12.4
           Distro: Ubuntu 18.04 LTS
Machine:   Device: portable System: Alienware product: Alienware 17 v: A08 serial: N/A
           Mobo: Alienware model: 04WT2G v: A00 serial: N/A UEFI [Legacy]: Alienware v: A08 date: 12/25/2013
Battery    BAT1: charge: 21.7 Wh 100.0% condition: 21.7/87.3 Wh (25%)
CPU:       Quad core Intel Core i7-4700MQ (-MT-MCP-) cache: 6144 KB
           clock speeds: max: 3400 MHz 1: 1131 MHz 2: 1183 MHz 3: 1232 MHz 4: 1212 MHz 5: 1147 MHz 6: 1304 MHz
           7: 1200 MHz 8: 1212 MHz
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK104M [GeForce GTX 780M]
           Display Server: x11 (X.Org 1.19.6 ) drivers: (unloaded: fbdev,vesa) FAILED: modesetting,nouveau
           Resolution: 1920x1080@60.01hz, 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile version: 4.5 Mesa 18.0.0-rc5
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller driver: snd_hda_intel
           Card-3 Plantronics driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card-1: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller driver: alx
           IF: eth0 state: down mac: ec:f4:bb:14:c9:45
           Card-2: Broadcom Limited BCM4352 802.11ac Wireless Network Adapter driver: wl
           IF: wlan0 state: up mac: 54:27:1e:86:2f:05
Drives:    HDD Total Size: 1080.2GB (73.3% used)
           ID-1: /dev/sda model: TOSHIBA_MQ01ABD1 size: 1000.2GB
           ID-2: /dev/sdb model: LITEONIT_DMT size: 80.0GB
Partition: ID-1: / size: 902G used: 722G (85%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 17.06GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A gpu: 42.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 354 Uptime: 7:08 Memory: 5233.8/15925.8MB Client: Shell (bash) inxi: 2.3.56 
```

free -m

```
gokul@gokul-Alienware-17:~/Desktop$ free -m
              total        used        free      shared  buff/cache   available
Mem:          15925        5064        6350        1019        4511       10136

```

---

