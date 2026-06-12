---
title: "Wifi connects initially then drops after 2 mins or so"
date: 2015-12-21
forum: General Help
---

### Post by aled2 on 2015-12-21
Hi there

I've been searching the forum for some help with my wifi connection. My Windows connection runs absolutely fine (dual-boot) but I'm having trouble when I use Ubuntu.

Internet pages will load for about the first 2 minutes and I can ping my router, but after that it seems to just cut out, despite being told I am still connected to my network.

I've tried a few things that people have suggested but can't seem to get anywhere. Can anyone offer me some help please? Will love you forever ;)

---

### Post by kc1di on 2015-12-22
could you give us a little more info on the wifi card your using?
Go to a terminal and run the following command if your not sure what card your using and post out put here:
```
inxi -FZ
```

Also run the wireless script in my signature after the card drops out and post the output.

---

### Post by synkan on 2016-02-19
Hello

I also face the same problem. I follow the steps outlined above.

output of inxi -FZ is as follows:

Inspiron-N4050:~$ inxi -FZ
System:    Host: tsharma-Inspiron-N4050 Kernel: 3.19.0-49-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Dell product: Inspiron N4050
           Mobo: Dell model: 0GGRV5 version: A07 Bios: Dell version: A07 date: 03/23/2012
CPU:       Dual core Intel Core i5-2450M CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) 
           Clock Speeds: 1: 1498.828 MHz 2: 2309.960 MHz 3: 2397.851 MHz 4: 861.230 MHz
Graphics:  Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller 
           Card-2: Advanced Micro Devices [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] 
           X.Org: 1.17.1 drivers: ati,radeon,intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile GLX Version: 3.0 Mesa 10.5.9
Audio:     Card: Intel 6 Series/C200 Series Family High Definition Audio Controller driver: snd_hda_intel 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-49-generic
Network:   Card-1: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) driver: ath9k 
           IF: wlan0 state: up mac: e0:06:e6:63:80:a3
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller driver: r8169 
           IF: eth0 state: down mac: 24:b6:fd:4e:ce:1a
Drives:    HDD Total Size: 500.1GB (15.1% used) 1: id: /dev/sda model: WDC_WD5000BPVT size: 500.1GB 
Partition: ID: / size: 19G used: 4.7G (27%) fs: ext4 ID: /boot size: 454M used: 70M (17%) fs: ext4 
           ID: /home size: 98G used: 66G (72%) fs: ext4 ID: swap-1 size: 4.20GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 55.0C mobo: 49.0C gpu: N/A 
           Fan Speeds (in rpm): cpu: N/A fan-2: 0 
Info:      Processes: 233 Uptime: 11 min Memory: 1091.1/3860.1MB Client: Shell (bash) inxi: 1.9.17

The output of the wireless script is as below[ATTACH]267384[/ATTACH]

---

