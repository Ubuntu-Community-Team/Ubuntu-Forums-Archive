---
title: "trouble mounting webcam with udev rule"
date: 2008-04-30
forum: General Help
---

### Post by taslinux on 2008-04-30
I want to mount a USB webcam as a video device, but I'm having trouble in Gutsy (7.10).

lsusb gives me the idVendor (0932) & idProduct (1100) with the camera plugged in.

I then created this rule in /etc/udev/rules.d/:

KERNEL=="video*",SYSFS{idVendor}=="0932",SYSFS{idProduct}=="1100",SYMLINK+="webcam"

After reloading rules, unplugging and replugging the webcam, no new video device appears in /dev, and Camorama reports that it can't find /dev/video0.

What does happen when the cam gets plugged is that a set of empty x-special/device-char files appears in /dev corresponding to the USB bus. They're named usbdev5.5-X, where X=00,81,82,83 and 84.

Am I doing something wrong? Any idea how to get the cam recognised as a video device?

---

