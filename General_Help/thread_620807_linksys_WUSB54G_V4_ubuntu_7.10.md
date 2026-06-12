---
title: "linksys WUSB54G V4 ubuntu 7.10"
date: 2007-11-23
forum: General Help
---

### Post by xray15 on 2007-11-23
I found out the IdProduct for the V4 is 000d so i did 
```
BUS=="usb", SYSFS{idProduct}=="000d", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

I get error when i connect the device
```
device descriptor read/8, error -71
device not accepting address 8, error -71
```

I did what the tut says and my WUSB54G still turns on for a few secs then turns off

I have no idea why its doing this and i realy like to use ubuntu on my computer

**My WUSB54G v4 works fine on windows on the same PC but not on ubuntu and ndiswrapper is installed with the right drivers.**

> Getting WUSB54GS to Work in Edgy, Feisty, and Gutsy
If you are an Edgy user, I've got some bad news and good news. You are going to have to configure your system to work with the WUSB54GS. The good news is that once this configuring is done, you'll never have to worry about it again (until you reinstall or upgrade).

The basics of the problem is that Edgy has a new "feature" that limits the power that goes to USB devices. This is all well and good to protect USB devices, except when a device wants more power then the kernel likes. The WUSB54GS is one of those devices.

This feature can be turned off. Here's how.

NOTE: Please do not have your device plugged in until the end of this tutorial!

Open up a terminal, and punch in the following:
Code:

sudo nano -w /etc/udev/rules.d/99-custom.rules

A new blank file opens up. Type in the following text. Keep the text as one line - do not let it wrap over to the next line.
WUSB54GS v1:
```
BUS=="usb", SYSFS{idProduct}=="000e", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

WUSB54GS v2:
```
BUS=="usb", SYSFS{idProduct}=="0014", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

Type Ctrl+O, the ENTER key, then Ctrl+X. You are now done!

What did we just do? Well, the system that tracks for new devices is called udev. This system has a set of rules under /etc/udev/rules.d/. What we did was add a rule that said "If this device's product is 000e, and the idVendor is 13b1, run this command". The command forces Linux to use configuration choice #1 (which so happens to be ndiswrapper) for this device. The variable $devpath marks where the device's folder is. It took me months to figure this whole thing out, but it was worth every bit of it. 

I did so many howto's and non of them work and i am freaking out because i try to get this to work for MONTHS

---

### Post by mahousaru on 2007-11-23
Just to let you know my WUSB54Gv4 works in Gutsy out of the box.  I just plug it in and add my WPA key and it connects via the rt2500usb driver with no effort on my part.  I just tried it with the built in USB port and on the powered hub and have no power issues with it.

---

### Post by xray15 on 2007-11-23
Will its does not work fine on my pc because it turns on for a few secs then it turns off and i realy like to use my ubuntu again

---

### Post by xray15 on 2007-11-24
bump

---

### Post by xray15 on 2007-11-24
My pc did not have internet for a few days now because of this :(

---

