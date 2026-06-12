---
title: "Modify USB API for Google Chrome..."
date: 2016-07-16
forum: General Help
---

### Post by ebozzz on 2016-07-16
Ok, here is my issue. I'm a musician who uses Peterson Tuners. Peterson allows me to be able to manage the devices that I own via a Chrome app that's called [Peterson Connect]("https://www.petersontuners.com/connect/"). Unfortunately, my tuners are not detected from a Linux platform. I opened a support ticket with Peterson and their most recent reply provided me with the information below from the Caveats section of the following URL....

> **Caveats**

Not all devices can be accessed through the USB API. In general, devices are not accessible because either the Operating System's kernel or a native driver holds them off from user space code. Some examples are devices with HID profiles on OSX systems, and USB pen drives.

On most Linux systems, USB devices are mapped with read-only permissions by default. To open a device through this API, your user will need to have write access to it too. A simple solution is to set a udev rule. Create a file /etc/udev/rules.d/50-yourdevicename.rules with the following content:

SUBSYSTEM=="usb", ATTR{idVendor}=="[yourdevicevendor]", MODE="0664", GROUP="plugdev"

Then, just restart the udev daemon: service udev restart. You can check if device permissions are set correctly by following these steps:

Run lsusb to find the bus and device numbers.
Run ls -al /dev/bus/usb/[bus]/[device]. This file should be owned by group "plugdev" and have group write permissions.
Your app cannot do this automatically since this this procedure requires root access. We recommend that you provide instructions to end-users and link to the Caveats section on this page for an explanation.

On Chrome OS, simply call usb.requestAccess. The permission broker does this for you.

Content available under the CC-By 3.0 license
GoogleTerms of ServicePrivacy PolicyReport a content bug

[https://developer.chrome.com/apps/app_usb#caveats](https://developer.chrome.com/apps/app_usb#caveats)

I get that I need to create a file named "50-yourdevicename.rules" within the directory /etc/udev/rules.d. That file should include the following information....

SUBSYSTEM=="usb", ATTR{idVendor}=="[yourdevicevendor]", MODE="0664", GROUP="plugdev"

Here's where I'm a little lost. In the brackets following ATTR, what should be entered for the "idVendor" and also "yourdevicevendor"? Any insight would be much appreciated. Thanks!

---

### Post by gordintoronto on 2016-07-16
Could you post the output of this command: lsusb

When I run it, one of the lines says:
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

The "ID" identifies the vendor and product. One of the ways I might use this is in a Google search, such as: 0ac8:303b usb linux

---

### Post by ebozzz on 2016-07-17
Here it is.....

> :~$ lsusb
Bus 004 Device 003: ID 3938:1031  
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 064e:d281 Suyin Corp. 
Bus 003 Device 003: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by gordintoronto on 2016-07-17
The Peterson person expected the devices to show up in lsusb. Do they have an external power supply? How about a power switch?

---

### Post by ebozzz on 2016-07-17
> **gordintoronto said:**
> The Peterson person expected the devices to show up in lsusb. Do they have an external power supply? How about a power switch?

Got you. I can connect them and then run the command again. One is powered by USB or it's internal battery and the other is 9 volt DC/battery that also has USB connectivity.

---

