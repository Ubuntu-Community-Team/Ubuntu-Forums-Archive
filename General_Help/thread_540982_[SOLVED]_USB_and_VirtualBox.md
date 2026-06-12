---
title: "[SOLVED] USB and VirtualBox"
date: 2007-09-02
forum: General Help
---

### Post by fjgaude on 2007-09-02
Anyone have an answer to why USB devices are recognized in VB but we get:

> Not permitted to open the USB device, check usbfs options.

I've done all the help file states requiring permissions and updating the mountkernfs.sh file. Still no-go. Wonder if the host system needs to be disconnected from the devices?

Any suggestions? Help...

frank

---

### Post by fjgaude on 2007-09-02
Sovled this issue through VB forums... here's how:

add yourself to the vboxusers group created when you installed VirtualBox and note the gid, here for me it was 1002. Then add line in fstab file:

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

And also add this line in /etc/init.d/mountkernfs.sh:

## Mount the usbfs for use in Virtual Box
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=1002,devmode=664

That's it... got my printers to work as they work in Windows. Hurray!

VirtualBox seems to have it all as a workstation, free too.

frank

---

