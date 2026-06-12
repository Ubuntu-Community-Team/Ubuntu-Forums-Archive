---
title: "Can't figure out why udev rule isn't working..."
date: 2007-08-28
forum: General Help
---

### Post by peitschie on 2007-08-28
Hi,

I've been attempting to create a udev rule to automatically link my phone up and mount it, but am running into issues getting the udev rule to do anything at all!

I am currently putting the following code into /etc/udev/user.rules

> ACTION=="add", SUBSYSTEM=="usb", ATTR{manufacturer}=="Sony Ericsson", ATTR{product}=="Sony Ericsson K608i", SYMLINK="mobile"


The information for the filter was found using udevinfo on the correct USB device in /sys/class/usb_devices...<etc>...

The annoying thing is, if I remove the SYMLINK command and use udevtest on it, the rule responds.  But the instant I put the SYMLINK command back in, the rule stops ever being referenced.  Am I doing something wrong here?

---

### Post by Steve1961 on 2007-08-28
> **peitschie said:**
> Hi,

I've been attempting to create a udev rule to automatically link my phone up and mount it, but am running into issues getting the udev rule to do anything at all!

I am currently putting the following code into /etc/udev/user.rules



The information for the filter was found using udevinfo on the correct USB device in /sys/class/usb_devices...<etc>...

The annoying thing is, if I remove the SYMLINK command and use udevtest on it, the rule responds.  But the instant I put the SYMLINK command back in, the rule stops ever being referenced.  Am I doing something wrong here?

Try this:

ACTION=="add", SUBSYSTEM=="usb", ATTR{manufacturer}=="Sony Ericsson", ATTR{product}=="Sony Ericsson K608i", SYMLINK+="mobile"

---

### Post by peitschie on 2007-08-28
Hi Steve,

I have just added that as you recommended... still no go though.  Udevtest shows no response on the rule, and in "real life" no changes are made either.

---

### Post by peitschie on 2007-08-28
Here is the udevinfo for the device I am attempting to recognise:

> 
root@haven:/etc/udev# udevinfo -ap /sys/class/usb_device/usbdev1.1/device/1-1

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/class/usb_device/usbdev1.1/device/1-1':
    KERNEL=="1-1"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{serial}=="356841005256307_0"
    ATTR{product}=="Sony Ericsson K608i"
    ATTR{manufacturer}=="Sony Ericsson"
    ATTR{maxchild}=="0"
    ATTR{version}==" 2.00"
    ATTR{devnum}=="5"
    ATTR{speed}=="12"
    ATTR{bMaxPacketSize0}=="64"
    ATTR{bNumConfigurations}=="1"
    ATTR{bDeviceProtocol}=="00"
    ATTR{bDeviceSubClass}=="00"
    ATTR{bDeviceClass}=="02"
    ATTR{bcdDevice}=="0000"
    ATTR{idProduct}=="d017"
    ATTR{idVendor}=="0fce"
    ATTR{bMaxPower}==" 20mA"
    ATTR{bmAttributes}=="c0"
    ATTR{bConfigurationValue}=="1"
    ATTR{bNumInterfaces}==" 8"
    ATTR{configuration}==""


---

### Post by Steve1961 on 2007-08-29
Weird!  Perhaps worth trawling through this link to see if you can find an answer:

[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

### Post by peitschie on 2007-08-29
Hi Steve,

Thanks for the link.  That was actually what I was using to come up with the brief line I did :).

I'm going to keep scratching my head over this I guess... oh well... I can hack together a script to do it instead.  A little less secure, but useable all the same.

Thanks for your help!

---

