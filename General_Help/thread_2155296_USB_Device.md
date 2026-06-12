---
title: "USB Device"
date: 2013-06-17
forum: General Help
---

### Post by alfirdaous on 2013-06-17
Hello everybody,

I've noticed this last 2 days, my Ubuntu is not detecting any USB device, I am using Ubuntu 13.04.

```

$ lsb_release
No LSB modules are available.
$ uname -a
Linux ubuntu 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

Thx in advance

---

### Post by Bashing-om on 2013-06-17
[COLOR=#000000]alfirdaous; Hi !
That out put is normal, mine:
> 
sysop@1304mini:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 13.04
Release:        13.04
Codename:       raring
sysop@1304mini:~$


To see what your system sees for usb devices. try:
```
lsusb
```
with usb devices plugged in.
[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by alfirdaous on 2013-06-17
this is the output:

```

$ lsusb
Bus 001 Device 002: ID 0d49:7250 Maxtor 
Bus 002 Device 004: ID 1307:0163 Transcend Information, Inc. 256MB/512MB/1GB Flash Drive
Bus 002 Device 002: ID 0408:030c Quanta Computer, Inc. HP Webcam
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Bashing-om on 2013-06-17
[COLOR=#000000]alfirdaous; 

usb devices are recognized ........what is the specifics of your query ?

[/COLOR]

---

### Post by alfirdaous on 2013-06-18
I tried to install a package name, then it says cannot be installed because of a kernal probleme, I installed the kernel.... (I forgot the name), then restarted, now it works great.

Thx

---

