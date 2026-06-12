---
title: "Key repeat broken"
date: 2017-10-09
forum: General Help
---

### Post by myfluxi on 2017-10-09
After one week on fresh install of 17.04 I upgraded to artful on a Medion notebook. I'd be a really happy camper, but unfortunately key repeat is unusable. I can enable and disable and change settings with some effect but most of the time I'm getting only 2-5 repetitions or none at all. Is this a known bug? What do I need to provide to get some suggestions?

---

### Post by ajgreeny on 2017-10-09
Are you sure it is not a hardware problem; can you try a live OS on the laptop to see if it's the same problem?

---

### Post by myfluxi on 2017-10-09
It was fine in 17.04. xset -q says:
```
  auto repeat delay:  250    repeat rate:  62  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
```

I tried a mainline kernel in zesty and had to configure libinput to get tap to click et al; the issue with key repeat was there as well.

---

### Post by myfluxi on 2017-10-10
After some more digging: Key autorepeat broken when booting a Live OS, it's working nicely when booting a zesty 4.10.0-35 kernel image.

Would this be a kernel issue? I'm looking at the [i8042]("http://kernel.ubuntu.com/git/ubuntu/ubuntu-artful.git/log/drivers/input/serio") code and logs but I see no relevant changes.

---

### Post by dixonstalbert on 2017-10-22
I did a fresh install of 17.10 from 16.04 on my laptop and had same issue

; repeat keys now unresponsive or lock up after typing a burst of 5-10 repetitions. no change with changing gui settings or xset or gsettings.

Booting into alternative 17.10 low-latency  kernel makes no difference, or booting in ubuntu.xorg,  but booting into 4.10.0-994 xenial kernel immediately fixes problems without touching settings.

I also cannot see any error messages anywhere. Should I file a bug report anyway?

---

### Post by wildmanne39 on 2017-10-22
@dixonstalbert please create your own thread in the appropraite section of the forum instead of posting in someone else's thread and 17.10 has been released so this is not the appropriate forum for posting about 17.10.

Thanks

---

### Post by 1jarwolf on 2017-10-22
I wish to add to this thread if I may. I will paste a following link with the specs of my computer. I am also having this non repeat meaning, I can only press a letter and it will only give it an out put of a single letter.

Link to my specs:     [http://paste.ubuntu.com/25799041/](http://paste.ubuntu.com/25799041/)

---

### Post by cariboo on 2017-10-23
> **1jarwolf said:**
> I wish to add to this thread if I may. I will paste a following link with the specs of my computer. I am also having this non repeat meaning, I can only press a letter and it will only give it an out put of a single letter.

Link to my specs:     [http://paste.ubuntu.com/25799041/](http://paste.ubuntu.com/25799041/)

We usually use inxi to publish system specs:

```
 inxi -F
```

results in:

```
inxi -F
System:    Host: alexis Kernel: 4.13.0-16-generic x86_64 bits: 64
           Desktop: Xfce 4.12.3 Distro: Ubuntu 17.10
Machine:   Device: laptop System: TOSHIBA product: Satellite C50-B v: PSCMLC-02Y00T serial: N/A
           Mobo: TOSHIBA model: ZBWAA v: 1.00 serial: N/A
           UEFI: TOSHIBA v: 1.70 date: 12/11/2014
Battery    BAT1: charge: 25.4 Wh 100.0% condition: 25.4/31.7 Wh (80%)
CPU:       Quad core Intel Pentium N3530 (-MCP-) cache: 1024 KB
           clock speeds: max: 2582 MHz 1: 2165 MHz 2: 2165 MHz 3: 2165 MHz
           4: 2165 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: x11 (X.Org 1.19.5 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel Bay Trail version: 4.2 Mesa 17.2.2
Audio:     Card Intel Atom Processor Z36xxx/Z37xxx Series High Def. Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card-1: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169
           IF: enp1s0 state: down mac: f8:a9:63:7a:e4:e3
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k
           IF: wlp2s0 state: up mac: b8:ee:65:8a:1b:f7
Drives:    HDD Total Size: 256.1GB (13.4% used)
           ID-1: /dev/sda model: ADATA_SP920SS size: 256.1GB
Partition: ID-1: / size: 19G used: 8.4G (49%) fs: ext4 dev: /dev/sda2
           ID-2: /home size: 215G used: 24G (12%) fs: ext4 dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 53.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 188 Uptime: 6 days Memory: 1916.4/3835.0MB
           Client: Shell (bash) inxi: 2.3.37 
```

---

### Post by myfluxi on 2017-10-23
Maybe this thread could be moved to the general section now.

As a workaround I enabled Settings / Universl Access / Typing Assist / Slow Keys at minimal acceptance delay. This way I'm getting key autorepeat in browsers and some apps. It's annoyingly broken in gedit, terminal etc.

---

### Post by cariboo on 2017-10-23
Moved by request.

---

