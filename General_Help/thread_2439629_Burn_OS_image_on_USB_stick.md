---
title: "Burn OS image on USB stick"
date: 2020-03-30
forum: General Help
---

### Post by satimis on 2020-03-30
Hi all,

I forgot which application shall I run burning an OS image on USB```

"Make Startup Disk" ???

```
Activities -> startup up

instead of running following command on Terminal```

sudo dd bz=4M if=/home/username/Downloads/2012-10-28-wheezy-raspbian.img of=/dev/sdc

```

I'm prepared to burn Raspberry-stretch image on a SD card which has been plugged into USB port.  Then the SD card can be booted on Raspberry Pi 3

Please advise.  Thanks

---

### Post by ipv on 2020-03-30
> **satimis said:**
> I forgot which application shall I run burning an OS image on USB

1. gnome-multi-writer

2. usb-creator-gtk

---

### Post by ajgreeny on 2020-03-30
I would suggest that [mkusb]("https://help.ubuntu.com/community/mkusb") is the best way forward.

I think most users are now using it; I certainly haven't used anything else for a long time.

---

### Post by satimis on 2020-03-30
Lot of thanks for your advice.

usb-creator-gtk is built-in

It can be started by;
Activities -> startup disk

as mentioned on my original posting.

Regards
satimis

---

