---
title: "HDD indicator starts glowing constantly &amp; PC freezes"
date: 2020-11-13
forum: General Help
---

### Post by linuxyogi on 2020-11-13
HDD indicator starts glowing constantly & PC freezes. The only running app is Firefox streaming an Youtube video. This does not happen all the time but when it happens the only way out is to use REISUB. Any ideas how to troubleshoot this ? I first noticed this issue while using Arch so I thought Arch's bleeding edge nature may be the cause so I installed Ubuntu but same thing is happening.

```
$ inxi -Fxz
System:    Host: mrubuntu Kernel: 4.15.0-123-generic x86_64
           bits: 64 gcc: 7.5.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.5 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: H110M-CS v: Rev X.0x serial: N/A
           UEFI: American Megatrends v: 3016 date: 12/27/2016
CPU:       Dual core Intel Core i3-6100 (-MT-MCP-) 
           arch: Skylake-S rev.3 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 14799
           clock speeds: max: 3700 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz
           4: 800 MHz
Graphics:  Card: Intel HD Graphics 530 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1366x768@59.96hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 530 (SKL GT2)
           version: 4.6 Mesa 20.0.8 Direct Render: Yes
Audio:     Card Intel 100 Series/C230 Series Family HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-123-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: down mac: <filter>
           Card-2: Ralink MT7601U Wireless Adapter
           driver: mt7601u usb-ID: 001-004
           IF: wlp0s20f0u7 state: N/A mac: N/A
Drives:    HDD Total Size: 120.0GB (30.6% used)
           ID-1: /dev/sda model: Samsung_SSD_750 size: 120.0GB
Partition: ID-1: / size: 24G used: 8.0G (36%) fs: ext4 dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 260 Uptime: 28 min Memory: 1663.1/3810.5MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.201) inxi: 2.3.56 


```

---

### Post by linuxyogi on 2020-11-20
I have replaced Ubuntu 18.04  with Lubuntu 20.04 but the same thing is happening again. Is 4GB of ram too little ?

---

### Post by CatKiller on 2020-11-20
> **linuxyogi said:**
> Is 4GB of ram too little ?

It's not great. I wouldn't have gone for less than 8 for any of my machines for the last 10 years or so.

Linux does handle being out of memory quite badly, and it would look like what you're describing, and hitting the swap hard would cause your activity light to be pegged on. There is work underway to improve that situation. 

There are tools you can use to monitor your memory usage and, if it is memory pressure that you're experiencing, ad blockers / script blockers might help to lower the memory footprint of your browser.

---

### Post by CelticWarrior on 2020-11-20
There's something else at play there.

While the above is true, the "toy" computer I'm using to post this also has only 4GB of RAM (DDR3L), coupled with an entry level Celeron. More often than not I have a few tabs open in Firefox AND Chromium, usually one of those is Youtube, plus a couple of bloated news feeds, plus Transmission, plus the heavyweight Java based JDownloader and occasionally one or two office files open... Sometimes I'm also running updates at the same time... Occasionally other random software as well... Believe it or not it works fine and smooth >99% of the time.

In summary, I would be checking your Firefox addons before anything else.

---

