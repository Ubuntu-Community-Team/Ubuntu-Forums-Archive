---
title: "USB to Serial adaptors - can't get my system to recognize them"
date: 2013-06-30
forum: General Help
---

### Post by Rsxhawk on 2013-06-30
I have a handful of USB to Serial adaptors that I'd like to use on my Ubuntu system since I have quite a few cisco/juniper lab devices that I would love to access the console on through Ubuntu, but the adaptors I have don't necessarily have drivers for Linux, or if they do, they say its built into Linux.  I am just trying to use Putty and open a serial connection, but when I try to open the session using any of the available tty or usb0 connections, it says it can't open the session and that permission was denied.  Is there a simple user/group permission issue I can resolve to allow my system to use these adaptors?  

Thanks,
Rsxhawk

---

### Post by zero2xiii on 2013-06-30
Hay,

Firstly, you need root (sudo) access to access usb/serial devices in my experience. So start there.

Secondly, you need to find the resulting device when you connect a class-compliant device. You can do that with plugging in the device then:

```
tail /var/log/syslog
```

after which you can use a terminal app and open the device eg "ttyUSB0". Remember sudo...

Cheers and good luck.

---

### Post by Rsxhawk on 2013-06-30
Here's the output of the syslog from when I plugged in the usb to serial adaptor:

user@localhost:~$ tail /var/log/syslog
 kernel: [3730896.303216] usb 2-1.5.1: new full-speed USB device number 16 using ehci_hcd
kernel: [3730896.396102] pl2303 2-1.5.1:1.0: pl2303 converter detected
kernel: [3730896.397720] usb 2-1.5.1: pl2303 converter now attached to ttyUSB0
mtp-probe: checking bus 2, device 16: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5.1"
mtp-probe: bus: 2, device: 16 was not an MTP device

---

### Post by Rsxhawk on 2013-06-30
Well I took your advice, went into terminal and launched putty from there using "gksu putty", then authenticated, then opened ttyUSB0 via the serial option in Putty and it worked.  Thanks again!

---

### Post by zero2xiii on 2013-07-01
Hay,

My pleasure, please mark your thread as solved if you would please :)

Cheers

---

