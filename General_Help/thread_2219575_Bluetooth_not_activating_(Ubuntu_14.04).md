---
title: "Bluetooth not activating (Ubuntu 14.04)"
date: 2014-04-24
forum: General Help
---

### Post by Hvidemose on 2014-04-24
I have a problem with Bluetooth not activating. There is no icon by the watch. When i open the preinstalled app, it appears as off. When i switch i to on and/or activate "Show Bluetooth in menu bar", nothing happens. If close the window at open it again, its on off again.

How can i get it to work?

---

### Post by sandyd on 2014-04-24
> **Hvidemose said:**
> I have a problem with Bluetooth not activating. There is no icon by the watch. When i open the preinstalled app, it appears as off. When i switch i to on and/or activate "Show Bluetooth in menu bar", nothing happens. If close the window at open it again, its on off again.

How can i get it to work?

What bluetooth card is this?

Post the output of
```

lspci 
lsusb
```

---

### Post by Hvidemose on 2014-04-24
Well it comes up with:

```
whiteboy@whiteboy-U31SD:~$ lspci 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce GT 520M] (rev ff)
04:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
whiteboy@whiteboy-U31SD:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 052: ID 13d3:5710 IMC Networks UVC VGA Webcam
Bus 001 Device 003: ID 13d3:3304 IMC Networks Asus Integrated Bluetooth module [AR3011]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
whiteboy@whiteboy-U31SD:~$
```

---

### Post by sandyd on 2014-04-24
Sounds like [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/714862](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/714862) / [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/822128](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/822128) though there is no indication that it is an issue in trusty

---

### Post by Hvidemose on 2014-04-24
Ah, ok. So it will probably be fixed along the way?

---

### Post by majk2 on 2014-05-30
I also cannot switch Bluetooth on in system settings in Ubuntu 14.04 on my Alienware M17X R2 running the following bluetooth:
ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)



"No Bluetooth adaptors found"

---

### Post by public-mosteo on 2014-06-03
Exact same problem as OP with 

ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)| t

---

### Post by Chinmay_B on 2014-06-03
Go to system Settings and search for "bluetooth" you will get the bluetooth icon near the clock after you will try to put it on

---

### Post by jeremy31 on 2014-06-03
```
lsmod | grep ath9k
```
If you see ath9k in the results, try ```
sudo modprobe -r ath9k
``` ```
sudo modprobe ath9k btcoex_enable=1
```

You should be able to see if it works by going to /sys/module/ath9k/parameters in your file manager and see if btcoex_enable has a 1 on the icon, then see if bluetooth works

---

### Post by majk2 on 2014-06-13
> **Chinmay_B said:**
> Go to system Settings and search for "bluetooth" you will get the bluetooth icon near the clock after you will try to put it on

No I mean that when you go into settings and choose bluetooth you can't switch it on it just says "No Bluetooth adapters found"

---

### Post by majk2 on 2014-06-13
> **jeremy31 said:**
> ```
lsmod | grep ath9k
```
If you see ath9k in the results, try ```
sudo modprobe -r ath9k
``` ```
sudo modprobe ath9k btcoex_enable=1
```

You should be able to see if it works by going to /sys/module/ath9k/parameters in your file manager and see if btcoex_enable has a 1 on the icon, then see if bluetooth works
If I use "lsmod | grep ath9k" in terminal nothing happens
But when I used just "lsmod" I got a whole lot of info but presume this is what you need to know (does this mean anything to you?):
      bluetooth             395423  10 bnep,rfcomm

---

### Post by doylefermi on 2014-10-31
Its enabled still i cant get my bluetooth to work. The device scans but fails to find any device. Should I post any output?

---

### Post by frogotronic on 2015-10-29
I followed these instructions here and Bluetooth now works:

[http://askubuntu.com/questions/614319/ubuntu-15-04-bluetooth-no-adapters-found-dell-precision-m4800](http://askubuntu.com/questions/614319/ubuntu-15-04-bluetooth-no-adapters-found-dell-precision-m4800)

---

