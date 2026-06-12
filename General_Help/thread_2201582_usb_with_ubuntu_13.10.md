---
title: "usb with ubuntu 13.10"
date: 2014-01-25
forum: General Help
---

### Post by glenberg on 2014-01-25
Hi I have a usb device that is a cycling computer that I can't get to work with ubuntu can anyone help me
Just noticed that I'm running a very new version of ubuntu well I'm really running ubuntu 13.10

---

### Post by tfrue on 2014-01-25
Are you getting any error messages? Anything that pops up on the Dash showing the USB? If no, then open a terminal by hitting 'ctrl+alt+t', unplug and plug back in the USB and type:
```
dmesg | tail
```
Also, post the output with the device plugged in:
```
sudo lsusb
and
sudo fdisk -l
```
Thanks,
Chris

---

### Post by sudodus on 2014-01-25
Welcome to the Ubuntu Forums :-)

Please describe your USB device! What is a cycling computer? How do you expect to connect to it? Is it working with Windows or MacOS? If you tell us more about the problem, we can give better tips and advice.

---

### Post by glenberg on 2014-01-25
chris@chris-desktop:~$ dmesg | tail
[ 7394.462950] usb 5-2: Product: CycleOps Joule GPS
[ 7394.462955] usb 5-2: Manufacturer: CycleOps
[ 7394.462959] usb 5-2: SerialNumber: AM01C5L2
[ 7394.470010] ftdi_sio 5-2:1.0: FTDI USB Serial Device converter detected
[ 7394.470077] usb 5-2: Detected FT232RL
[ 7394.470082] usb 5-2: Number of endpoints 2
[ 7394.470087] usb 5-2: Endpoint 1 MaxPacketSize 64
[ 7394.470092] usb 5-2: Endpoint 2 MaxPacketSize 64
[ 7394.470097] usb 5-2: Setting MaxPacketSize 64
[ 7394.472061] usb 5-2: FTDI USB Serial Device converter now attached to ttyUSB0
chris@chris-desktop:~$ sudo lsusb
[sudo] password for chris: 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 005 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chris@chris-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000cc5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    41961779    20877466    7  HPFS/NTFS/exFAT
/dev/sda3        41961780    84534029    21286125   83  Linux
/dev/sda4        84534091   976768064   446116987    5  Extended
/dev/sda5        84534093   974663549   445064728+  83  Linux
/dev/sda6       974663613   976768064     1052226   82  Linux swap / Solaris
chris@chris-desktop:~$ 
end.........................
message from with in golden cheater
ERROR : Open Failed : Open Permission Denied

---

### Post by sudodus on 2014-01-25
OK, I found this when searching the internet for ***CycleOps Joule GPS***

[http://www.bikeradar.com/gear/category/accessories/gadgets/gps-devices/product/review-cycleops-joule-gps-47014/](http://www.bikeradar.com/gear/category/accessories/gadgets/gps-devices/product/review-cycleops-joule-gps-47014/)

So now I know what it is. I suspect that is interacts with a computer via some Windows specific software, that comes with the device (on a CD) or that you can download from the internet.

---

### Post by glenberg on 2014-01-25
I'm using a linux software called golden cheater. It plugs in via usb and also I can't use in garmion cycling computer that interats with a website it also plugs in via usb 
Garmin I can use it like a HDD and grab the work files, but not the cycleops computer

---

### Post by sudodus on 2014-01-25
You know more than I about those things. Unfortunately many manufacturers do no think they can make money by making their devices work with linux. Sometimes you are lucky, and it works anyway, like you explained that you can grab the work files from the Garmin device.

For this reason I have at least one Windows system available (to connect to hardware devices, that only work with Windows or MacOS).

---

### Post by glenberg on 2014-01-25
Golden Cheater say it will work and has been tested and used with the computer.
it is sort of working as I get
 ERROR : Open Failed : Open Permission denied
anyway thanks for looking and your input
Chris

 > **sudodus said:**
> You know more than I about those things. Unfortunately many manufacturers do no think they can make money by making their devices work with linux. Sometimes you are lucky, and it works anyway, like you explained that you can grab the work files from the Garmin device.

For this reason I have at least one Windows system available (to connect to hardware devices, that only work with Windows or MacOS).

---

### Post by sudodus on 2014-01-25
If we are lucky, someone will chip in an help you, someone who knows how to make linux work with your CycleOps Joule GPS

So good luck :-)

---

### Post by Herman on 2014-01-25
There are two apps I know of which can be installed in Ubuntu and can connect to a gramin GPS and display the GPS tracks, waypoints, etc. They are Google Earth and Quantum GIS. I'm not sure if those will be exactly what you're looking for but they might be worth a try. There are also GPSPrune, GPS Babel, and several other programs for working with GPS data.

EDIT: I found this link about Golden Cheetah, [http://goldencheetah.org/](http://goldencheetah.org/), if anyone else can help the OP a litle bit more. I'm abou to go off line for a few hours.

---

### Post by Herman on 2014-01-25
The Golden Cheetah docs say you might need to uninstall britty to get it working in Ubuntu, link: [http://goldencheetah.org/faq.html](http://goldencheetah.org/faq.html)
```
sudo apt-get remove brltty
```

---

### Post by glenberg on 2014-01-25
I think it is now more finding out how to get permission to read the Computer ( device ) as it seams to ubuntu reconises it but just will not let me read from it
When I connect the garmin computer up, Ubuntu adds it as a device but not with the cycleops computer

---

### Post by Herman on 2014-01-26
Alright, have a look at this link then, [Allowing your linux userid permission to use your usb device]("https://github.com/GoldenCheetah/GoldenCheetah/wiki/Allowing-your-linux-userid-permission-to-use-your-usb-device") (Golden Cheetah wiki, github). 

More here: [https://github.com/GoldenCheetah/GoldenCheetah/wiki/_pages](https://github.com/GoldenCheetah/GoldenCheetah/wiki/_pages)

---

