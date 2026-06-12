---
title: "A Possible UDEV And/Or EVDEV Regression?"
date: 2007-04-25
forum: General Help
---

### Post by Slalomsk8er on 2007-04-25
I have a Logitech MX Revolution mouse and by following the guide @ [http://ubuntuforums.org/showthread.php?t=277388]("http://ubuntuforums.org/showthread.php?t=277388")
I got it working but discovered, that if I make a udev rule like in the guide:```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../phys}=="usb-0000:00:02.0-4/input0", NAME="input/event9"
```
All is fine except that I need to always plug the receiver in to the same port, but if I use some thing like:```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../phys}=="usb-0000:00:02.0-4/input0", NAME="input/mxr"
```
I get a Preinit returned NULL error from X (after restarting udev and updating xorg.conf).
To me it looks like the Xorg evdev driver can now only handle "/dev/input/eventX" devices properly.

In the past (if I remember it right), I was able to use my old mx810 with udev and evdev under the location "/dev/input/mx810", in Gentoo and Ubuntu.
It would be good if someone with the needed knowledge could find the cause of this regression as I would like to use the "/dev/input/by_id/xyz" node to address my MX Revolution on what ever USB port the receiver is plugged in with out even writing a rule per possible USB port ;)

Thanks for every try.

---

