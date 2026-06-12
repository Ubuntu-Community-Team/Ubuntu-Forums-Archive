---
title: "Help me learn about using a usb-stick"
date: 2007-01-11
forum: General Help
---

### Post by ubix on 2007-01-11
I would like to use a usb-stick as a temporary file system, to copy files between unconnected systems. However, I do have a few questions. First of all I'd like to find a document describing installation and usage, explaining the following:

[list]
[*] are there special requirements to install such a device at the time when Linux is installed?
[*] Can I buy any such device and expect it to work?
[*] Does one need to create a disk partition and/or format a file system on a usb/stick?
[*] Which Ubuntu releases will work with usb-stick?
[/list]

---

### Post by mistypotato on 2007-01-11
Do you mean a USB thumb drive ?

Not exactly sure what you mean by "USB Stick" ?

---

### Post by meng on 2007-01-11
Dapper and Edgy work well with USB sticks, they should auto-mount most such devices.

---

### Post by haiku99 on 2007-01-11
I've used a few different brands with Dapper and Edgy with no problems.  There are a few points to remember....always eject the card properly before removing it (right click menu) or some files you copied to it may not really be on it, also deleted files go to a hidden trash folder on the drive, just choose "show hidden" if you need to see or delete the folder...

---

### Post by Seine on 2007-01-11
USB storage devices like these are handled very well by Ubuntu. When you insert the USB stick in it will automatically mount to something like /media/usbdisk and an icon will appear on your desktop. 

When you need to remove the device, right click the icon and choose eject. Or simply type *eject usbdisk* from the terminal. Compare this with the horrible 3 or 4 click removal process in Windows XP!

* if your USB disk has mounted to something other than /media/usbdisk then you'll replace "usbdisk" in the eject command with whatever is the mount location after /media/. E.G. eject usbdisk1

---

### Post by ubix on 2007-01-12
Thank you guys!

---

