---
title: "Speed up bootup"
date: 2017-08-22
forum: General Help
---

### Post by raleigh3 on 2017-08-22
I would like to speed up my boot up.


Can I do without any of these ?

```
Certificate and Key Storage

Mate Nvidia Optimus

Maximus Window Management
Onboard
Orca Screen Reader
Policy Kit Authentication Agent
PulseAudio Sound System
Secret Storage Service
Settings Overlay
SSH Key Agent


 

```

---

### Post by RobGoss on 2017-08-22
I would probably say **secret storage**, **Orca screen reader**, unless you're using any of these programs or services

---

### Post by Bucky Ball on 2017-08-22
You could delete bits and pieces, but why would that speed up boot and is that what you're even talking about? Switching off what services are booting with the machine *_may_* achieve a faster boot.

Are you talking about deleting stuff or stopping it booting with the system? You should check 'Session and startup' and switch off what you don't need to be started at boot if you haven't already.

You don't give much detail. This has just started happening? What are the specs on your machine? Did you install anything or do and update/upgrade and now you are getting slow boots?

---

### Post by raleigh3 on 2017-08-22
I like to get the best out of my system.

I assume startup applications mostly occur during bootup.

I am talking about stopping things that are NOT necessary for my system.

I did a search for Mate Nvidia Optimus, and found nothing. 

For instance, I stopped Bluetooth because Bluetooth does not work on my system.

I need some clarification for Session and Startup ?

My startup averages about 110 seconds.

Mate is my desktop, not XFCE.

---

### Post by again? on 2017-08-22
Are you talking about time to boot to the greeter or time for desktop to load after logging in?
systemd provides a tool called systemd-analyze that can be used to show timing details about the boot process.
[Improving performance/Boot process]("https://wiki.archlinux.org/index.php/Improving_performance/Boot_process")

---

### Post by raleigh3 on 2017-08-23
Dear Guber2, (I like your handle. :-) }

I am talking about the time from when I hit power button until my desktop shows up.

```
andy@7:~$ systemd-analyze blame
         27.195s apt-daily.service
         14.227s udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb2-2\x2d5.service
```

---

### Post by again? on 2017-08-23
How long does it take to get to the login screen.
If you have have autologin turned on in your account settings, turn it off 
and determine how long it takes to get to the greeter and then how long the desktop takes to load.

**Edit:** Also found this... [https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)
See what you get for just
```
systemd-analyze
```

eg my output
```
glen@GU17:~$ systemd-analyze
Startup finished in 3.169s (kernel) + 9.097s (userspace) = 12.266s
```

As you're using Mate this may be relevant.
[https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297](https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297)

---

### Post by Bucky Ball on 2017-08-23
More detail. 

> **Bucky Ball said:**
> You should check 'Session and startup' and switch off what you don't need to be started at boot if you haven't already.

If you have a heap of things booting with the session then that will delay your boot time. When you start Ubuntu you may be starting a whole lot of apps and services in the background that you don't need (and perhaps never will).

You want 'Session and Startup> Autostart applications'. Look through that list and disable what is not required to boot with the system. For instance, do you use bluetooth? Do you have the bluetooth service starting when you start your machine? If you don't use bluetooth you don't need that to happen at startup or ever. Waste of time and resources.

Personally, I do new installs with a base system (minimal install, which is just the Ubuntu kernel and nothing else, or Xubuntu-core which is a basic Xubuntu desktop and nothing else) and install what I need and want. That avoids 99.9% of unwanted cruft at startup and any other time.

Please provide details of your machine; make, model, processor and amount of RAM please.

---

### Post by vasa1 on 2017-08-23
> **Bucky Ball said:**
> ...
Please provide details of your machine; make, model, processor and amount of RAM please.
*inxi -F* will help. You need to install *inxi* as it isn't present by default.

---

### Post by raleigh3 on 2017-08-23
```
System:    Host: 7 Kernel: 4.4.0-92-generic x86_64 (64 bit) Desktop: MATE 1.12.1  Distro: Ubuntu 16.04 xenial
Machine:   System: Gigabyte product: N/A
           Mobo: Gigabyte model: F2A68HM-H v: x.x Bios: American Megatrends v: FB date: 04/22/2015
CPU:       Quad core AMD A8-7600 Radeon R7 10 Compute Cores 4C+6G (-MCP-) cache: 8192 KB 
           clock speeds: max: 3100 MHz 1: 1900 MHz 2: 1400 MHz 3: 2400 MHz 4: 1900 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Kaveri [Radeon R7 Graphics]
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD KAVERI (DRM 2.43.0 / 4.4.0-92-generic, LLVM 4.0.0)
           GLX Version: 3.0 Mesa 17.0.7
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Kaveri HDMI/DP Audio Controller driver: snd_hda_intel
           Card-3 Microsoft LifeCam HD-5000 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.4.0-92-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp1s0 state: up speed: 100 Mbps duplex: full mac: 40:8d:5c:44:af:9b
           Card-2: Qualcomm Atheros AR93xx Wireless Network Adapter driver: ath9k
           IF: wlp2s0 state: down mac: f8:1a:67:1d:ef:a2
Drives:    HDD Total Size: 2320.5GB (0.9% used) ID-1: /dev/sda model: WDC_WD2003FYPS size: 2000.4GB
           ID-2: /dev/sdb model: MAXTOR_STM332062 size: 320.1GB
Partition: ID-1: / size: 1.8T used: 12G (1%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 174 Uptime: 8:00 Memory: 809.4/6920.2MB Client: Shell (bash) inxi: 2.2.35
```

---

### Post by raleigh3 on 2017-08-23
I decided that 70 seconds is not that long for a startup.

Thanks for the help.

---

