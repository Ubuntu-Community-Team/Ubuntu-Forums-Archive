---
title: "Run Script On ANY USB Being Plugged In"
date: 2014-12-08
forum: General Help
---

### Post by crutchcorn on 2014-12-08
Hey guys, I am trying to run a script whenever anything is plugged into the USB ports. I am using Ubuntu 14.10 and I know I can use udev rules to do so. I currently made a file in /etc/udev/rules.d/, made it executable. This file shows:
```
ACTION=="add", SUBSYSTEM=="usb_device", RUN+="/etc/udev/script.sh
```
As you can see, I want to run a script called script.sh in /etc/udev/ (yes I made the script executable as well).
Any help? Sorry if this is a duplicate, but I've looked everywhere and cannot find how to properly do this (I've seen other answers, none work)

---

### Post by phidia on 2014-12-09
[This thread]("http://askubuntu.com/questions/401390/running-a-script-on-connecting-usb-device") might be useful to you-hope it is.

---

### Post by crutchcorn on 2014-12-09
> **phidia said:**
> [This thread]("http://askubuntu.com/questions/401390/running-a-script-on-connecting-usb-device") might be useful to you-hope it is.

This may just do it.... I'll have to check when I get home. Thanks a million! I was looking all over for an answer and things weren't working. :)

EDIT: Doesn't seem to work for me...

---

