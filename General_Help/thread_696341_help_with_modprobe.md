---
title: "help with modprobe"
date: 2008-02-13
forum: General Help
---

### Post by MDS2008 on 2008-02-13
Hi All,

I have managed to get my Telstra Next G wireless card working, but everytime after I reboot I have to run the following command before I can connect to the internet.

sudo modprobe usbserial vendor=0x19d2 product=0x0001

Can anyone tell me how to set this up automatically?

Thanks

---

### Post by xarquid on 2008-02-13
Greetings,

I recommend you:

> sudo nano /etc/init.d/boot.local

Add the line:

> modprobe usbserial vendor=0x19d2 product=0x0001

At the end of the file.

Save.

And this will be executed upon each boot.

Enjoy your Ubuntu experience ;-)

Sincerely,

x

---

### Post by SpaceTeddy on 2008-02-14
/etc/modules is exactly for the purpose of loading modules at boot time.. 

gksu gedit /etc/modules

put your line there without the modprobe... so simply add
> usbserial vendor=0x19d2 product=0x0001

---

### Post by MDS2008 on 2008-02-15
Thanks SpaceTeddy

That worked perfectly!

---

### Post by gatherp on 2008-02-15
I am doing exactly the same (ZTE MF622 HSDPA modem), and I know that this will work, but will that cause problems with other devices that use the usbserial module?

I can get the device working after modifying the instructions posted by OOZIE about the HUAWEI e220 on other forums, which puts udev rules in place to get it to ignore the storage device (I'm running Dapper still), and then trigger a modprobe install usbserial with the vendor and device parameters followed by a call to wvdial, but I can't help but think that there should be a better way of doing this.

The device does not automatically get picked up as a usbserial device, possibly because the USB information does not show it as that class of device (I'm feeling my way here, because I'm not that familier with udev). I tried haching it into the modules.usbmap, and this allowed the system to detect that it needed the usbserial module, but of course, this does not persist across reboots (there must be a depmod somewhere in the startup).

If someone can point me to a good tutorial of how this all hangs together, I will look into it myself (Googling it produces so many hits, most of which are people asking similar questions on forums).

Of course, by the time I work it out, Gutsy will probably be out, and I will be upgrading!

In the meantime, I can post the modified udev rules and callout scripts if anybody wants.

---

