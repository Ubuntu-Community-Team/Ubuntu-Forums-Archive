---
title: "How to edit a file?"
date: 2007-03-17
forum: General Help
---

### Post by neogeek on 2007-03-17
Hi,
I am trying to connect my Canon s50 but keeps getting this error message:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I found a solution on the web, and I cannot seems to edit the file that I need to. Here is what I am suppose to do:

Add to /etc/udev/rules.d/45-libgphoto2.rules a line with that info, e.g.:
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05a2", MODE="0660", GROUP="plugdev"

I cannot seems to edit the file from the terminal. I tried using gedit and still cannot save the file after I add what I am suppose to add.

Would appreciate any help on edit a file. Thanks!

:confused:

---

### Post by peabody on 2007-03-17
sudo gedet /etc/udev/rules.d/45-libgphoto2.rules

You'll be prompted for a password.  Type your user password and hit enter.

---

### Post by aysiu on 2007-03-17
If you prefer the terminal: ```
sudo nano -B /etc/udev/rules.d/45-libgphoto2.rules
``` or if you're using Ubuntu: ```
gksudo gedit /etc/udev/rules.d/45-libgphoto2.rules
``` or if you're using Kubuntu: ```
kdesu kate /etc/udev/rules.d/45-libgphoto2.rules
``` or if you're using Xubuntu: ```
gksudo mousepad /etc/udev/rules.d/45-libgphoto2.rules
```

---

