---
title: "Mount USB File System in Ubuntu 11.10 (Oneiric Ocelot)"
date: 2012-10-22
forum: General Help
---

### Post by JAG Franco on 2012-10-22
Hi

I've Ubuntu 11.10 (Oneiric Ocelot)
I can't mount /proc/bus/usb, because don't exists the folder /proc/bus/usb.

Thanks you...

---

### Post by cariboo on 2012-10-23
Moved to General Help. Your question has nothing to do with Ubuntu application Development

---

### Post by ~LoKe on 2012-10-23
> **JAG Franco said:**
> Hi

I've Ubuntu 11.10 (Oneiric Ocelot)
I can't mount /proc/bus/usb, because don't exists the folder /proc/bus/usb.

Thanks you...
Please explain how you're trying to mount the USB device.

---

### Post by JAG Franco on 2012-10-23
For mount the devices, I use the commands:
mount -t usbfs none /proc/bus/usb
mount -t usbdevfs none /proc/bus/usb
but it say me that the point for mount doesn't exists.

Then, I use these commands for create the folder:
mkdir /proc/bus/usb
mkdir -p /proc/bus/usb
sudo mkdir /proc/bus/usb
sudo mkdir -p /proc/bus/usb
but it say me that can't create the directory, doesn't exist the file or the directory.

I use the root user.

Thanks you.

---

### Post by Impavidus on 2012-10-23
/proc/ is not a normal part of your file system, but is meant to provide information on processes running on your computer. The directories in there change continuously as processes start or exit, so it doesn't surprise me you can't create a directory there. Check wikipedia for procfs for more info.

Anyway, the usb device should be listed somewhere in /dev/ when you plug it in (if that is what you are trying to do) and you should be able to mount it at some normal directory (/media/usbdisk/ or something like that should be the normal place). In my case the usb stick is at /dev/sdb and is automatically mounted at /media/B288-271C, which should be possible as well using
```
mount /dev/sdb /media/B288-271C
```My advice is to try and mount it somewhere in /media

---

### Post by JAG Franco on 2012-10-23
I need to mount the /proc/bus/usb because a program, that I can't move, work with this path. In Ubuntu 9.10 I can mount the devices without problems with the commands above.

Thanks you

---

