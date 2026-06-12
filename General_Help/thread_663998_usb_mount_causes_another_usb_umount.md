---
title: "usb mount causes another usb umount"
date: 2008-01-10
forum: General Help
---

### Post by dannemil on 2008-01-10
This is a strange one. I have multiple usb slots on my laptop. If I have one external hard drive mounted through one of the usb slots, and I plug in my ipod, it automatically unmounts the external hard drive and vice versa. I can then plug in the unmounted device and both stay mounted, but this is crazy.

This never happened before with 7.04, only started happening since I upgraded to 7.10. The two usb slots are not even on the same usb hub when this happens. Any help would be appreciated.

:confused:

---

### Post by archie78 on 2008-03-19
> This is a strange one. I have multiple usb slots on my laptop. If I have one external hard drive mounted >through one of the usb slots, and I plug in my ipod, it automatically unmounts the external hard drive and >vice versa. I can then plug in the unmounted device and both stay mounted, but this is crazy.

I've just noticed that the names of disks become altered, i.e., I also have USB key and external USB drive, the first one (USB key) always was /dev/sdb. Now, after I plugged in USB drive, my USB key became /dev/sdc. The moral of the story is that the names of two external devices might be exchanged resulting in the situation you see.
You can check if that's true by typing in terminal

sudo fdisk -l

That will show you the disks mounted.
Hope that helps.
Best...
archie78

---

