---
title: "Recurrent crash in system with new motherboard; better driver for wifi adapter?"
date: 2020-02-09
forum: General Help
---

### Post by MgFrobozz on 2020-02-09
I just installed a new motherboard into my system, and I've had a few crashes this week. I gratefully accept any suggestions for debugging.

The log below covers the instant that the problem occurred, while I was entering text into my editor (slickedit). All mouse and keyboard service locked up. I don't know whether this was the IO_PAGE_FAULT that caused the problem, or the cron job. There have been a number of IO_PAGE_FAULTS which didn't cause a crash, all in xhci_hcd, all in the same domain and at the same address. I am using realtek-supplied source for the kernel driver from [https://bit.ly/2IXCf8i](https://bit.ly/2IXCf8i) (the url given in the instructions for the AC2100 usb wifi adapter with vendor_id 0bda and device_id b812), which built and installed kernal module 88x2bu.

I'd like to try removing the 88x2bu driver and installing whatever is distribution-standard. If you have a system running the realtek wifi chip with the same vendor/device ID, could you give me the name of the driver?

Another crash possibility would be the cron job, the last thing logged before I rebooted. Anyone see a potential for lockup there? The sendmail system has been working well for me. It's currently running every 20 minutes.


```
[COLOR=#000000]> cat /var/log/syslog.1
Feb  8 11:33:44 localhost kernel: [171242.597802] xhci_hcd 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000d address=0x08000000fff04300 flags=0x0030]
Feb  8 11:39:01 localhost CRON[18088]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Feb  8 11:39:09 localhost systemd[1]: Starting Clean php session files...
Feb  8 11:39:09 localhost systemd[1]: Started Clean php session files.
Feb  8 11:40:01 localhost CRON[18158]: (smmsp) CMD (test -x /etc/init.d/sendmail && test -x /usr/share/sendmail/sendmail && test -x /usr/lib/sm.bin/sendmail && /usr/share/sendmail/sendmail cron-msp)
[/COLOR]

```

```

> inxi -F -x -N -i
System:    Host: aratas Kernel: 4.15.0-76-generic x86_64 bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4) Distro: Ubuntu 18.04.4 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: PRIME B450M-A v: Rev X.0x serial: N/A
           UEFI [Legacy]: American Megatrends v: 1820 date: 09/12/2019
CPU:       6 core AMD Ryzen 5 2600 Six-Core (-MT-MCP-) arch: Zen rev.2 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 40718
           clock speeds: max: 3400 MHz 1: 1437 MHz 2: 1432 MHz 3: 1377 MHz 4: 1359 MHz
           5: 1601 MHz 6: 1546 MHz 7: 1411 MHz 8: 1409 MHz 9: 1375 MHz 10: 1441 MHz
           11: 1551 MHz 12: 1554 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Oland PRO [Radeon R7 240/340]
           bus-ID: 08:00.0
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1280x1024@60.02hz
           OpenGL: renderer: AMD OLAND (DRM 2.50.0, 4.15.0-76-generic, LLVM 9.0.0)
           version: 4.5 Mesa 19.2.8 Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
           driver: snd_hda_intel bus-ID: 0a:00.3
           Card-2 Advanced Micro Devices [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
           driver: snd_hda_intel bus-ID: 08:00.1
           Sound: Advanced Linux Sound Architecture v: k4.15.0-76-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: f000 bus-ID: 07:00.0
           IF: enp7s0 state: up speed: 1000 Mbps duplex: full mac: a8:5e:45:57:05:9d
           WAN IP: 73.240.208.244
           IF: enp7s0 ip-v4: 10.0.0.2 ip-v6-link: N/A
           IF: wlx0013eff208da ip-v4: 192.168.100.100 ip-v6-link: fe80::9bbc:391e:4137:7cb9
Drives:    HDD Total Size: 8481.7GB (3.4% used)
           ID-1: /dev/sda model: KINGSTON_SA400S3 size: 480.1GB temp: 27C
           ID-2: /dev/sdb model: WDC_WD40EFRX size: 4000.8GB temp: 33C
           ID-3: /dev/sdc model: WDC_WD40EFRX size: 4000.8GB temp: 33C
Partition: ID-1: / size: 356G used: 116G (35%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 39.85GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      Device-1: /dev/md0 - active components: online: sdb2[0] sdc2[1]
           Info: raid: 1 report: 2/2 blocks: 1953275456 chunk size: N/A bitmap: true
Sensors:   System Temperatures: cpu: 30.0C mobo: N/A gpu: 23.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 364 Uptime: 17:04 Memory: 2669.5/32160.0MB
           Init: systemd runlevel: 5 Gcc sys: 7.4.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56 

```

```

> lshw 
...
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-76-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 4.15
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb
                      description: Generic USB device
                      product: 802.11ac NIC
                      vendor: Realtek
                      physical id: 4
                      bus info: usb@3:4
                      version: 2.10
                      serial: 123456
                      capabilities: usb-2.10
                      configuration: driver=rtl88x2bu maxpower=500mA speed=480Mbit/s
...



```

---

### Post by mörgæs on 2020-02-10
> **MgFrobozz said:**
> 
I'd like to try removing the 88x2bu driver and installing whatever is distribution-standard. 

That's also what I would suggest. How does it behave in a live boot of 19.10 / 20.04?

---

### Post by MgFrobozz on 2020-03-07
Thanks, mörgæs ... no faults at all after I reefed out that driver and used rtl8xxxu instead.

---

### Post by mörgæs on 2020-03-07
Good, please mark the thread solved.

---

### Post by MgFrobozz on 2020-03-19
[deleted inaccurate information]

---

