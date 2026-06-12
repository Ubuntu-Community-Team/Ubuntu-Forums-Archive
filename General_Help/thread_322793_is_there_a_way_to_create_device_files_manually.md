---
title: "is there a way to create device files manually?"
date: 2006-12-21
forum: General Help
---

### Post by grahams on 2006-12-21
I'm looking for a command to create device files after hot-pluging a disk drive into my system so I do not have to reboot. I know in HP-UX I can do this with an ioscan and an insf -e. Can I do this in Linux?

many thanks

Graham

---

### Post by ebash on 2006-12-21
Normally the kernel should create the device for you as soon as it detects it. With ubuntu you can use udev for controlling the device name and for creating symlinks for the device. 

Take a look at the man page of udev.

---

### Post by grahams on 2006-12-22
Thanks for the reply.

I have a scsi tape drive that isn't seen unless it is powered on at boot time. Is there a way to force udev to scan and create the device files? I could not see it in the man page.

---

### Post by az on 2006-12-22
> **grahams said:**
> Thanks for the reply.

I have a scsi tape drive that isn't seen unless it is powered on at boot time. Is there a way to force udev to scan and create the device files? I could not see it in the man page.

AFAIK, it is your hardware that limits it's immediate use.  Your BIOS has to know about it to make it available to the kernel.

---

### Post by grahams on 2006-12-22
I'm guessing udev will only add devices that natively support hotplug such as USB and doesn't notice a scsi device coming online. I'm trying to figure out how devices are found during boot so I can run that manually to add a device without rebooting. Commercial UNIX's such as HP-UX can do this (insf -e).

---

