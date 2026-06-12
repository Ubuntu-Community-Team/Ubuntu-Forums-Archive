---
title: "How can I mount my USB disk? Detected in lsusb but not in fdisk -l ?"
date: 2015-11-15
forum: General Help
---

### Post by okkadiroglu on 2015-11-15
I am experiencing the same problem so I will answer your questions.

[QUOTE=sudodus;13385345]I suggest some tests to try to identify what is wrong.

- Does the USB disk connect correctly in another computer (it can run linux, Windows or MacOS)?

I tried the usb drive with another Ubuntu 15.10 computer and it did not mount.

- Try connecting it in another USB port of the computer.

I tried all available usb ports on my computer and still does not mount.


- Try connecting it with another USB cable.

I do not use usb cables.


Other usb drives work properly and mount when I insert them into the computer usb ports.


Thanks for your help.

---

### Post by sudodus on 2015-11-15
You replied to these questions (in another thread).

> I suggest some tests to try to identify what is wrong.

- Does the USB disk connect correctly in another computer (it can run linux, Windows or MacOS)?

- Try connecting it in another USB port of the computer.
- Try connecting it with another USB cable.

- Try connecting it in your computer when it is booted from a CD/DVD/USB drive. This is testing if there is something wrong with the installed system.

What computer is it? Maybe someone here knows about the particular hardware in your computer and your particular USB disk - if there are known problems.

So please specify the brand name and model of the computer, or if it is more relevant, the motherboard.

Have you got some USB extension hub or similar?

Is there some other USB device connected? In that case you can disconnect it and only connect your USB disk.

In addition to that I would suggest that you

- insert/connect the USB drive

- run the following commands and post the output within [noparse]```
tags
```[/noparse] in a reply.

```
df
lsusb
sudo parted -ls
sudo lsblk -fm
```

I hope the output will help me and other people to identify your problem and suggest what to do

---

