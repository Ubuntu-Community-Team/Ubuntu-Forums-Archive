---
title: "How to get serial number from hardware"
date: 2020-11-20
forum: General Help
---

### Post by sincos2007 on 2020-11-20
By Ubuntu, how to get serial number from hardware or devices in or connected to Ubuntu pc. For example: mother board, memory, cpu, ide or sata hard disk, usb storage, usb dvd recorder, usb hub

Thanks

---

### Post by btindie on 2020-11-20
Take a look at [https://linux.die.net/man/8/dmidecode](https://linux.die.net/man/8/dmidecode) that should do what you want for the motherboard/cpu

For the disks you can use [https://linux.die.net/man/8/hdparm](https://linux.die.net/man/8/hdparm)
e.g.
```

# hdparm -i /dev/sda

```

---

### Post by sincos2007 on 2020-11-20
Thanks for your help. Is it possible to get serial number from usb devices connected to Ubuntu PC?

---

### Post by TheFu on 2020-11-20
> **sincos2007 said:**
> Thanks for your help. Is it possible to get serial number from usb devices connected to Ubuntu PC?

It depends on the device.

With storage, the S/N is part of the HW connection and in the **dmesg** logs.

My webcam does as well, but it is on a line alone, so connecting it to the webcam requires looking a few lines above or below the line that looks like this:
```
[218211.503423] usb 1-3: SerialNumber: 76B4Dxxx
```

inxi -xx -D -m
claims to get the disk and memory module S/N.  I'm seeing mixed results.

Normally, **lsusb** and **lspci** are the commands to see data on those sorts of devices.

I don't know of any way, similar to what MS-Windows has, that tracks every connected USB device ever plugged into the system until the OS is wiped. That doesn't mean it doesn't exist, just that I don't know if that happens.

---

