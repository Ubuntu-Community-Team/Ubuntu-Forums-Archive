---
title: "Toshiba Laptop, Hardy Heron"
date: 2008-05-01
forum: General Help
---

### Post by SlalomMan on 2008-05-01
I own a Toshiba Satellite A205-S4617, and I know there were some problems with it...wireless, sound, etc. I'm pretty sure Gutsy fixed my wireless problem (the card is a draft N), but I had to do some fiddling to get my sound to work. I want to install Hardy clean, but I don't want to risk losing my sound (although I suppose I could try to fix it again). Does anyone know if these are fixed by Hardy? I think the newest ALSA drivers might have done it...but I'm not sure. 

Thanks in advance!

---

### Post by Tom--d on 2008-05-01
Post the outcome of 

```
lspci
```
```
lsusb
```

and we shall see from there :)

---

### Post by SlalomMan on 2008-05-01
lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

My guess is my sound is:
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```
and my wireless card is:
```

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

```
lsusb
```

Bus 005 Device 005: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

I don't think lsusb is relevant in this case...as it only contains my camera and fingerprint reader.

---

### Post by Tom--d on 2008-05-01
The only reason I asked for lsusb was because my internal wireless card comes under usb :\

Will see what I can do.

---

### Post by Tom--d on 2008-05-01
Wireless will be easy.. 

All you will need is ndiswrapper and the windows drivers for that wireless card. 

In synpatic package manager, search for ndiswrapper.. 

you will get 3 results.. 

they are:

ndiswrapper common
ndiswrapper utils
ndisgtk

Install them all..

go to System > admin > windows wireless drivers

Download your windows wireless drivers for your card. 

Locate the .inf file and .sys file.

in 'Windows Wireless Drivers' locate the .inf file and click install..

Then wireless will just start to work.. (depends on the driver, and if its the right one.)

Post back for more help on it..


I will look into sound as intel are good with linux.. mm

---

### Post by SlalomMan on 2008-05-01
Alright...I don't think I did much with my sound except installing the latest version of ALSA and then blacklisting all of the modem drivers...because at one time "aplay -l" would return my modem in addition to my sound card. I'm not sure which one really worked, but I guess I can try again. Probably what I'll end up doing is creating a partition and installing hardy on there, making sure I can get everything configured right, and then deleting my old partition.

---

### Post by Tom--d on 2008-05-01
Did the wireless work?


With sound:

do this and make sure everything is full 

```
gnome-volume-control
```

It happened to me before. I thought my sound didnt work and i found out my PCM was on 0 xD

---

### Post by SlalomMan on 2008-05-01
I haven't installed hardy yet...I guess over the weekend I'll install it and give you an update on how it went.

Thanks!

---

