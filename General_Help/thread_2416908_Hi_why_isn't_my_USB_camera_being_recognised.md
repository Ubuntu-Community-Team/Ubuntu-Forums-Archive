---
title: "Hi why isn't my USB camera being recognised"
date: 2019-04-17
forum: General Help
---

### Post by iamtheeggman2 on 2019-04-17
i cant use two webcam programs i actually did install they say no video camera provided!

clearly though it is listed second up from the bottom

```
home@home-System-Product-Name:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 001 Device 002: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 0a16:1200 Trek Technology (S) PTE, Ltd 
Bus 008 Device 007: ID 1b3b:2936 iPassion Technology Inc. PC Camera/Webcam controller
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by NM5TF on 2019-04-17
we could certainly use more information before even starting to help....

what 2 "webcam programs" are you attempting to use ???

what about your hardware ???

with the camera plugged in, post the output of ```
inxi -F
```

and then post the output of 

```
sudo lsusb -v -d 1b3b:2936
```

use code tags to make the reply more readable...use the [COLOR="#FF0000"]ADV Reply button[/COLOR], select the [COLOR="#FF0000"]#[/COLOR] from the menu & paste the output between the [COLOR="#FF0000"]#[/COLOR] characters...

further research tells me the camera may NOT be compatible with Linux....  

[https://ubuntuforums.org/showthread.php?t=1333503&page=2](https://ubuntuforums.org/showthread.php?t=1333503&page=2) post # 11

tommy

---

### Post by oldrocker99 on 2019-04-17
Does Cheese see the camera? It's either already installed or not, so get it and/or try it.

---

### Post by iamtheeggman2 on 2019-04-18
```
home@home-System-Product-Name:~$ inxi -F
System:    Host: home-System-Product-Name Kernel: 4.15.0-47-generic i686
           bits: 32
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.2 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: M5A78L-M/USB3 v: Rev X.0x serial: N/A
           BIOS: American Megatrends v: 0801 date: 11/30/2011
CPU:       8 core AMD FX-8350 Eight-Core (-MCP-) cache: 16384 KB
           clock speeds: max: 4000 MHz 1: 1420 MHz 2: 1407 MHz 3: 1403 MHz
           4: 1404 MHz 5: 1405 MHz 6: 1404 MHz 7: 1404 MHz 8: 1404 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV710 [Radeon HD 4350/4550]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1024x768@60.00hz, 1024x768@60.00hz
           OpenGL: renderer: AMD RV710 (DRM 2.50.0 / 4.15.0-47-generic, LLVM 7.0.0)
           version: 3.3 Mesa 18.2.8
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-47-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp3s0 state: down mac: c8:60:00:12:7d:6d
           Card-2: NetGear WG111v3 54 Mbps Wireless [realtek RTL8187B]
           driver: rtl8187
           IF: wlx00223ffc8c16 state: N/A mac: N/A
Drives:    HDD Total Size: 638.0GB (2.7% used)
           ID-1: /dev/sda model: WDC_WD5000AVDS size: 500.1GB
           ID-2: /dev/sdb model: DOGFISH_SSD_120G size: 120.0GB
           ID-3: USB /dev/sdc model: TDMINIG4 size: 2.0GB
           ID-4: USB /dev/sdd model: Cruzer_Fit size: 15.8GB
Partition: ID-1: / size: 27G used: 6.8G (27%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 38.0C mobo: 34.0C gpu: 44.5
           Fan Speeds (in rpm): cpu: 822 sys-1: 0
Info:      Processes: 215 Uptime: 10 min Memory: 486.1/10100.8MB
           Client: Shell (bash) inxi: 2.3.56 
home@home-System-Product-Name:~$ 


```

but nothing from the following command:-


```
home@home-System-Product-Name:~$ sudo lsusb -v -d 1b3b:2936
home@home-System-Product-Name:~$ 


```

thanks in advance

further research tells me the camera may NOT be compatible with Linux....  

[https://ubuntuforums.org/showthread....1333503&page=2]("https://ubuntuforums.org/showthread.php?t=1333503&page=2") post # 11

:-(

well i might have to look for windows software, do any of you have experience using windows software that can do time lapse?

wow, I just tried a usb endoscope which worked in linux puppy would you believe, yet doesn't on my far more advance setup, here i the outputs with it connected

btw using chees and guvcview

it doesnt even list it lol

```
home@home-System-Product-Name:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 001 Device 002: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

the device i have is

[https://www.amazon.co.uk/COOCHEER-Waterproof-Borescope-Endoscope-Inspection/dp/B01CQQMXDM](https://www.amazon.co.uk/COOCHEER-Waterproof-Borescope-Endoscope-Inspection/dp/B01CQQMXDM)

---

### Post by dre2fresh on 2019-04-18
Have you tried installing **cheese**
sudo apt-get install cheese

---

### Post by NM5TF on 2019-04-18
> 

<snip>
but nothing from the following command:-


```
home@home-System-Product-Name:~$ sudo lsusb -v -d 1b3b:2936
home@home-System-Product-Name:~$ 


```

thanks in advance

that is a major problem...:mad:

when you ran lsusb, the output looked correct...:KS

```
Bus 008 Device 007: ID 1b3b:2936 iPassion Technology Inc. PC Camera/Webcam controller
```

yet when you ran the sudo lsusb -v -d 1b3b:2936 command, it didn't communicate with the camera for some reason....:confused::confused:

looking like your camera is not compatible with Linux....:(

tommy

---

### Post by iamtheeggman2 on 2019-04-21
Today I tried this again because as you can see on my othe thread the cheese camera software now works, and now it can be seen with the command:

```
home@home-System-Product-Name:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 001 Device 004: ID 090c:037c Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 300k Pixel Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 0a16:1200 Trek Technology (S) PTE, Ltd 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
home@home-System-Product-Name:~$ 


```

i wonder if this is because the cable has been plugged into a different usb port?
I wonder if everything on the motherboard is installed properly now???

This command still presents noting, what does it mean anyway?

```
home@home-System-Product-Name:~$ sudo lsusb -v -d 1b3b:2936
home@home-System-Product-Name:~$ 


```

---

### Post by dino99 on 2019-04-21
Maybe be you should glance at relative error inside journalctl, and possibly install / use a more recent kernel, like 5

[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

you need headers (2) + image + modules (2) for your config (amd (64) or i380 (32) )
Download them into a subdir, then install them from that subdir with > sudo dpkg -i *

Often newest kernel support devices that older kernel does not.

---

### Post by iamtheeggman2 on 2019-04-21
> **dino99 said:**
> Maybe be you should glance at relative error inside journalctl, and possibly install / use a more recent kernel, like 5

but I have the latest ubuntu on here?

---

### Post by mörgæs on 2019-04-21
No, you have Ubuntu 18.04 which is two releases old.

You could try a live boot of 19.04 to see if anything has changed.

---

### Post by iamtheeggman2 on 2019-04-21
Well I installed it because this is the lasted long term support version. I was under the impression I'd be asking for trouble installing a bleeding edge one.

---

### Post by mörgæs on 2019-04-22
I am not suggesting that you install it now, just test it in a live boot. 

*If* the bug has been fixed in 19.04 (we don't know yet) then one can't be sure that the fix has trickled down to 18.04.

---

