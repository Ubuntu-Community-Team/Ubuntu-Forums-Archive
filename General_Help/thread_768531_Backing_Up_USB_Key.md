---
title: "Backing Up USB Key"
date: 2008-04-26
forum: General Help
---

### Post by punkle on 2008-04-26
Hey, 

I want to start backing up my college work which I keep on a USB key. Is it possible to setup a backup to run on the USB key whenever it is plugged into the computer.

I am currently running Ubuntu 7.10

Thank You.

---

### Post by ryanhaigh on 2008-04-26
You can change the application launched when a device is plugged in under system>preferences>removable drives and media. However I don't think you will be able to set rules for a single device there (im assuming you use more than 1 usb), to do this you will need to use and modify udev rules for your device. [This link]("http://gentoo-wiki.com/HOWTO_Customizing_UDEV") has info on how you can do that, setup a udev rule to  have the device use the same node every time then use the RUN option (see the autocalibrate joystick section) to run a script which copies everything from the drive.

---

