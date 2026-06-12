---
title: "hdtv usb tuner"
date: 2012-11-14
forum: General Help
---

### Post by ubunjay1 on 2012-11-14
hello i am new to ubuntu so forgive me for been such a noob at this just wanted to know how to install a hdtv usb tuner  to ubuntu 12.10  cant it been done or there any other hdtv app so i can wacth tv on ubuntu:confused:

---

### Post by dannyboy79 on 2012-11-14
what usb HD tv tuner is it? post the output of the following command entered into a terminal session

```
lsusb
```

---

### Post by ubunjay1 on 2012-11-14
jason@jason-laptop:~$ lsusb
Bus 002 Device 002: ID 187f:0201 Siano Mobile Silicon Nova B
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

the usb tuner is a npg real hdtv nano  the software that come with it is for windows and its need media 9 or higher to run oh and run the progame useing wine on ubuntu 12.10

---

### Post by grahammechanical on 2012-11-14
You may find that wine may not be any good at using the TV tuner. You may find that a Linux/Ubuntu application is better. Use the Ubuntu Software Centre and search for TV.

It all depends whether there is a driver for that USB device. And that is not always the case. With these devices it is best to buy a device that you know is supported.

[http://www.linuxtv.org/wiki/index.php/Tuners:_Supported_Tuners]("http://www.linuxtv.org/wiki/index.php/Tuners:_Supported_Tuners")

Regards.

---

### Post by dannyboy79 on 2012-11-14
check this command

```
dmesg | grep DVB
```

and check out this link because I believe you have the same siano nova b chipset
[http://linuxtv.org/wiki/index.php/CVOC-E121#Patch_for_Kernel_Source](http://linuxtv.org/wiki/index.php/CVOC-E121#Patch_for_Kernel_Source)

---

### Post by ubunjay1 on 2012-11-15
Hey thanks for the help ok so i try the command you told me to put in nothing happen and i went and had a look in the software center on ubuntu to find a tv app i got two mytv and digitel tv setup both said i had no tuner pluged it

---

### Post by dannyboy79 on 2012-11-15
if dmesg | grep DVB didn't return anything that means that the usb tuner isn't recognized by the kernel so no module is loaded. The link I provided talks about patching the kernel and installing the correct firmware. All that is above my head so I can't help. It would be pointless to install a tv app before you get the usb tv stick recognized by the kernel.
Good luck

---

