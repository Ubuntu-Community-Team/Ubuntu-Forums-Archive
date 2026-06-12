---
title: "Usb tv device"
date: 2013-01-24
forum: General Help
---

### Post by zackubunt on 2013-01-24
Hello everybody,i need a help installing usb tv device on ubuntu operating system.i also have driver on a cd but it won't work any help will be appreciated.thanks

---

### Post by Double.J on 2013-01-24
Hi there, could you provide more information I on the USB tuner being used? 

In the mean time, just check ubuntu can't find a driver for you. With it connected, click on the cog wheel, then system settings, then look for additional drivers.

Finally if no luck, could you also check that ubuntu can see the stick by typing this into terminal
```
lsusb
```

Cheers

---

### Post by zackubunt on 2013-01-25
> **gnu/mirow said:**
> hi there, could you provide more information i on the usb tuner being used? 

In the mean time, just check ubuntu can't find a driver for you. With it connected, click on the cog wheel, then system settings, then look for additional drivers.

Finally if no luck, could you also check that ubuntu can see the stick by typing this into terminal
```
lsusb
```cheers

thanks for reply.i have got usb tv device from danny model no u-1000.i also been to system setting and to additional drivers and couldn't find any thing,
will try to read from terminal and will post with reply.

---

### Post by zackubunt on 2013-01-25
> **zackubunt said:**
> thanks for reply.i have got usb tv device from danny model no u-1000.i also been to system setting and to additional drivers and couldn't find any thing,
will try to read from terminal and will post with reply.
also did a terminal and found Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b066 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 1f71:3301

---

### Post by furything on 2013-01-25
Sorry Zacubunt but I don't think there is a linux driver

see
[http://linuxtv.org/wiki/index.php/Hardware_Device_Information](http://linuxtv.org/wiki/index.php/Hardware_Device_Information)

I always check here first before buying a new dvb-t or dvb-s2 card.

Cannot see your device anywhere which suggests there is no driver yet.

---

### Post by zackubunt on 2013-01-25
Many thanks all of you.

---

