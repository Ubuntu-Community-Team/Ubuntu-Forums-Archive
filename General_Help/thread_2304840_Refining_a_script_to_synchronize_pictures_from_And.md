---
title: "Refining a script to synchronize pictures from Android phone to Ubuntu desktop."
date: 2015-11-30
forum: General Help
---

### Post by Roasted on 2015-11-30
Hi friends. After a long and tedious struggle with getting various sync clients to work with auto-syncing my pictures/videos to my NAS, I finally gave up. Despite running ownCloud at home, there were some issues with really large (1 GB+) videos hanging during the ownCloud sync. Other apps tend to work somewhat well but have their own limitations. As I worked through this process I got to the point where I realized even if I do get something successful with one of these apps, I would still be limited by the wifi speed. This became apparent when I did a manual phone sync and fell in love all over again with just how braindead fast USB (2.0 even) was with syncing these items. I ultimately thought I could just whip up a script, tie an icon to it, a desktop file, and essentially make my own application for it and be done with it. That way I could plug in the phone, launch the application, and that'd be it.

It's very basic and of course a work in progress, but here's what I got:

```
#!/bin/bash
set -e
notify-send "Camera Phone Sync Started"
rsync -a /run/user/1000/gvfs/gphoto2:host=%5Busb%3A001%2C007%5D/DCIM /home/$USER/Pictures/Camera-Phone-Sync/
notify-send "Camera Phone Sync Complete"
exit

```

The part I'm questioning is the rsync line. While this works great, I have to question something. I have two phones. My wife has one phone. I got to thinking it'd be nice if I could adapt this script to somehow detect what device is plugged in and sync that accordingly. That way if my Motorola Droid is plugged in, it knows to go to /media/user/MOT to rsync, while on the S3, it would do that goofy /run/user/1000 line posted above, and finally with my wife's S4, it would detect that and sync accordingly.

Anybody have any ideas how I can take essentially 3 possible mount points and if detected, sync accordingly? That way I could have one script to rule whatever device we may be working with to sync the items in question.

Thanks for any assistance!

---

### Post by sandyd on 2015-11-30
There is actually a whole set of things you can do to make it work quite well if you work with udev.

I borrowed a phone from somewhere and plugged it in:
Running lsusb give me 
```
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 008: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0bda:5756 Realtek Semiconductor Corp. 
Bus 001 Device 009: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
USB Device of my phone is 009, Bus is 001

My device path is now /dev/bus/usb/001/009

Lets make udevadm grab some info:
```

~$ udevadm info -q path -n /dev/bus/usb/001/009
/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3

```

```

~$ udevadm info -a -p /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3
<snip>
  looking at device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3':
    KERNEL=="1-1.3"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{authorized}=="1"
    ATTR{avoid_reset_quirk}=="0"
    ATTR{bConfigurationValue}=="1"
    ATTR{bDeviceClass}=="00"
    ATTR{bDeviceProtocol}=="00"
    ATTR{bDeviceSubClass}=="00"
    ATTR{bMaxPacketSize0}=="64"
    ATTR{bMaxPower}=="96mA"
    ATTR{bNumConfigurations}=="2"
    ATTR{bNumInterfaces}==" 1"
    ATTR{bcdDevice}=="0400"
    ATTR{bmAttributes}=="c0"
    ATTR{busnum}=="1"
    ATTR{configuration}==""
    ATTR{devnum}=="9"
    ATTR{devpath}=="1.3"                                                                                                                                                                        
    ATTR{idProduct}=="6860"                                                                                                                                                                     
    ATTR{idVendor}=="04e8"                                                                                                                                                                      
    ATTR{ltm_capable}=="no"                                                                                                                                                                     
    ATTR{manufacturer}=="Android"                                                                                                                                                               
    ATTR{maxchild}=="0"                                                                                                                                                                         
    ATTR{product}=="Android"                                                                                                                                                                    
    ATTR{quirks}=="0x0"                                                                                                                                                                         
    ATTR{removable}=="removable"                                                                                                                                                                
    ATTR{serial}=="75bf29b8"                                                                                                                                                                    
    ATTR{speed}=="480"
    ATTR{urbnum}=="13"
    ATTR{version}==" 2.00"
<snip>

```

We now have a serial number to identify the phone along with some other info!

We can create a script to run each time this particular device is plugged in. In the below example, I just set one ATTR to match, but you can add as many as you want, seperated by commas.

Place the following in /etc/udev/rules.d. Name the file like 10-<name>.rules. Replace <name> with your desired file name. I think it loads the rules in order of number like in GRUB.
```

SUBSYSTEMS=="usb", ATTRS{serial}=="75bf29b8", RUN+="/path/to/script"

```

The above instructions may have to be modified to suit your setup.

---

