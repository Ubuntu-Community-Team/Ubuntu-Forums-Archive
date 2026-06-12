---
title: "How To Reactivate a Blacklisted Module?"
date: 2013-12-28
forum: General Help
---

### Post by airilsra on 2013-12-28
Hi all, 

I have just upgraded my Ubuntu installation to 13.10 and it is working great. But yesterday I make a big mistake. In an attempt to uninstall dialer for my USB mobile broadband (Huawei EC176-2) I blacklisted module "option". I did that because when I installed dialer software, it show this error.
```
Fatal: module option is in use.
```

What i didn't know of is that module "option" is needed to detect a USB modem. So, my modem is not detected now. I blacklisted the module by making file */etc/modprobe.d/blacklist *(not */etc/modprobe.d/blacklist.**conf**) *and add this line:
```
blacklist option
```
and then 
```
sudo update-initramfs -u
```

I have tried to undo this change by deleting the blacklist line and even removing */etc/modprobe.d/blacklist. *But module "option" still not loaded on start up. I also tried to load module manually by:
```
sudo modprobe option
```
(and also load it's dependencies manually usbserial and usb_wwan)
but it is not help to detect my USB modem (ttyUSB1-3 is not detected). 

But if I boot to Windows or OpenSuse first and later restart to Ubuntu my modem is magically detected. I don't understand why.

---

### Post by 3rdalbum on 2013-12-28
From your last sentence, it is apparent that Ubuntu does not have the firmware for the device. Windows and OpenSuse do, so once they have loaded the firmware to the device you can use it in Ubuntu, at least until you unplug it or turn off the computer.

Get the firmware and put it into the appropriate place on Ubuntu and everything should work.

---

### Post by airilsra on 2013-12-28
@3rdalbum

I don't know what firmware and where to download. The modem was automatically detected by network-manager before i blacklist "option".

When it's detected lsusb shows this output:
*Bus 002 Device 002: ID 12d1:1505 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard*

When it's not it shows:
*Bus 002 Device 002: ID 12d1:140c Huawei Technologies Co., Ltd. E180v*

---

