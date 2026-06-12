---
title: "How to install logitech webcam ?"
date: 2022-04-15
forum: General Help
---

### Post by Tom_Carr on 2022-04-15
I just go a logitech webcam for my ubuntu desktop.  I can't find any linux software for it.  There is a page with software for windows to download, but nothing for linux that I can find.

I will probably only be using this for zoom.

---

### Post by deadflowr on 2022-04-15
It probably works out of the box.
Open Cheese and test it.
Cheese is still a default app, isn't it?

---

### Post by Tom_Carr on 2022-04-15
Yes !  Cheese is a default ap.  i opened it and see myself looking into the camara.

---

### Post by Tom_Carr on 2022-04-15
So it works with cheese but it doesn't work with zoom.  How can I track down the issue?

---

### Post by TheFu on 2022-04-15
Here's the command that I use to crop/zoom my webcam :
```
$ v4l2-ctl -d /dev/video0 -c zoom_absolute=200
```
The device changes based on other video devices in the system and which is seen/plugged in first.
Not all webcams support the zoom_absolute option, so different models from different vendors will have different support for the 50+ options that v4l2-ctl can modify.

The system it is connected into is 18.04.  The device shows up in the **dmesg** output as:
```
 usb 1-3: Product: HD Pro Webcam C920
 uvcvideo: Found UVC 1.00 device HD Pro Webcam C920 (046d:082d)
 input: HD Pro Webcam C920 as /devices/pci0000:00/0000:00:01.3/0000:01:00.0/usb1/1-3/1-3:1.0/input/input24
```

Open a terminal and run **dmesg -w**
Plug in the webcam.  Wait a few seconds. As the device is seen, recognized, drivers will be loaded automatically.  If not, then it doesn't have built-in support from kernel drivers. Ouch.  If it were me, I'd return whatever device it is immediately.  Life is too short to deal with hardware that doesn't support Linux out of the box.

Another way to get info about a USB device is by running ...
```
$ lsusb -v | egrep -i [COLOR="#008000"]webc[/COLOR]
Bus 001 Device 014: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
  idProduct          0x082d HD Pro Webcam C920

```
BTW, I don't have 14 USB devices connected to the system. Only 2 are connected (keyboard and webcam). The green webc is just a filter to limit the hundreds of detailed lines to something that has "webc" in the line, case insensitive.

---

### Post by deadflowr on 2022-04-16
> **Tom_Carr said:**
> So it works with cheese but it doesn't work with zoom.  How can I track down the issue?

Zoom from the Software Store?
Looking at the reviews for it in Ubuntu Software the current stable version has a lot of 1 and 2 star reviews with mentions of it being broken.
The version is also a snap version. So there is that, make of it what you will.

You can install the non-snap deb version, but you need to download it from zoom directly: [https://zoom.us/download?os=linux]("https://zoom.us/download?os=linux")
(If downloading it from zoom, you only need to set the linux type to Ubuntu. The other settings should auto set to 64-bit and 16.04+.
Don't worry about it saying 16.04+ as it means all versions of Ubuntu from 16.04 to the latest)

Double clicking on it should open the software installer app to allow installing it, though I'm not sure what version of Ubuntu you are running and whether that works for you or not.

You might want to uninstall the snap version too, as both version will show in the apps menu, which can get confusing; unless you like confusion.

---

