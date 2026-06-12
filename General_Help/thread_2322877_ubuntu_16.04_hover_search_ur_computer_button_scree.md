---
title: "ubuntu 16.04 hover search ur computer button screen flashes"
date: 2016-05-01
forum: General Help
---

### Post by jen8 on 2016-05-01
hi in my new installation of ubuntu 16.04, the desktop works strange.

there is a  search ur computer bottom at top left. when my mouse hover over it, the whole screen starts to flash strange patterns. If I start to type into the keywords box, the flashing starts again. I can barely see the detail of the search window.

I also have main menus of gimp and gedit disappear. I post thread about that yesterday and later I found out it was a bug of the desktop. can I get some more traditional desktop environment?

---

### Post by $yl9pAR%t on 2016-05-01
I suggest installing Ubuntu MATE 16.04 if you are looking for other DE, but before you will do it, paste here output of below terminal command to show us your hardware info.

```
inxi -b
```

---

### Post by jen8 on 2016-05-01
> **mefisto888 said:**
> I suggest installing Ubuntu MATE 16.04 if you are looking for other DE, but before you will do it, paste here output of below terminal command to show us your hardware info.

```
inxi -b
```

This is my output

System:    Host: pc Kernel: 4.4.0-21-generic x86_64 (64 bit) Desktop: N/A
           Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: OptiPlex 740 serial: DCV2W1S
           Mobo: Dell model: 0HX340 v: A01 serial: ..CN708217CDL1OA.
           Bios: Dell v: 2.1.6 date: 05/04/2008
CPU:       Dual core AMD Athlon 64 X2 4400+ (-MCP-) speed/max: 1000/2300 MHz
Graphics:  Card: NVIDIA C51 [GeForce 6150 LE]
           Display Server: X.org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa)
           tty size: 80x24 Advanced Data: N/A for root
Network:   Card-1: Broadcom NetXtreme BCM5754 Gigabit Ethernet PCI Express
           driver: tg3
           Card-2: Ralink RT5370 Wireless Adapter driver: rt2800usb
Drives:    HDD Total Size: 80.0GB (8.5% used)
Info:      Processes: 201 Uptime: 1:18 Memory: 1076.4/1935.3MB
           Client: Shell (bash) inxi: 2.2.35

---

### Post by $yl9pAR%t on 2016-05-01
OK, I know this GPU and I have to say sorry but you should give up on Ubuntu because Compiz do not want to work with GF6150 when using proprietary nvidia-304 driver. Nouveau driver (your case) works but system is very slow because of very high CPU usage.

Your hardware is very good to run Ubuntu Mate 16.04 64-bit and Xubuntu 16.04 64-bit. In this case, you can install nvidia-304 driver after OS installation.

---

### Post by Edwin_Rodriguez on 2016-05-01
Various graphical glitches happends to me.
After about 10 minutors of usage of Terminator the screen start to flash strange showing black lines and all screen moving making desktop unusable. Reboot solves the problem.
Also happends with VirtualBox.

My machine is a Dell Inspiron 14

lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
06:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

---

### Post by jen8 on 2016-05-01
> **mefisto888 said:**
> OK, I know this GPU and I have to say sorry but you should give up on Ubuntu because Compiz do not want to work with GF6150 when using proprietary nvidia-304 driver. Nouveau driver (your case) works but system is very slow because of very high CPU usage.

Your hardware is very good to run Ubuntu Mate 16.04 64-bit and Xubuntu 16.04 64-bit. In this case, you can install nvidia-304 driver after OS installation.

Thanks for the info of Ubuntu Mate,

---

### Post by jen8 on 2016-05-03
> **mefisto888 said:**
> OK, I know this GPU and I have to say sorry but you should give up on Ubuntu because Compiz do not want to work with GF6150 when using proprietary nvidia-304 driver. Nouveau driver (your case) works but system is very slow because of very high CPU usage.

Your hardware is very good to run Ubuntu Mate 16.04 64-bit and Xubuntu 16.04 64-bit. In this case, you can install nvidia-304 driver after OS installation.

Hi I installed Ubuntu mate, but it don't let me install gimp in the GUI place for download new software, the error message is about wrong package name. Also where do download nouveau driver for ubuntu mate?

---

### Post by $yl9pAR%t on 2016-05-04
> [COLOR=#000000]but it don't let me install gimp in the GUI place for download new software[/COLOR]

Please clarify the above. Are you talking about "Software Boutique"? In Ubuntu MATE the first place to go, when you want to install a popular software is "Software Boutique" (System -> Administration -> Software Boutique).

Nouveau driver is installed by default, you do not have to care about it, but it is good idea to install nvidia-304(tested) driver, to accomplish it, go to Software&Updates and choose Additional Drivers, wait for a while (be patiente) and you will see earlier mentioned nvidia driver. Tick it and apply. After installation reboot system.

---

### Post by mörgæs on 2016-05-06
Another option for the 6150 is accepting closed-source drivers during installation. It works for Lubuntu but I have not tried Mate, though.

---

### Post by jen8 on 2016-05-06
> **mefisto888 said:**
> Please clarify the above. Are you talking about "Software Boutique"? In Ubuntu MATE the first place to go, when you want to install a popular software is "Software Boutique" (System -> Administration -> Software Boutique).

Nouveau driver is installed by default, you do not have to care about it, but it is good idea to install nvidia-304(tested) driver, to accomplish it, go to Software&Updates and choose Additional Drivers, wait for a while (be patiente) and you will see earlier mentioned nvidia driver. Tick it and apply. After installation reboot system.

Yes, i mean software boutique. It doesn't work. Thanks for the info of the driver, I will test it.
I am also wondering if Ubuntu mate can run java in a browser? Detail is in an other post of mine [http://ubuntuforums.org/showthread.php?t=2322718](http://ubuntuforums.org/showthread.php?t=2322718)

---

### Post by $yl9pAR%t on 2016-05-06
I had no problems (ever) to install GIMP from Software Center in Ubuntu (Software Boutique in Ubuntu MATE), hence my question is, did you make update after OS installation? If not, go to Software Updater and do it (reboot OS after that).

Additionaly, please paste here outputs of the following terminal commands:

```
inxi -b
```

```
apt-cache policy gimp
```

---

