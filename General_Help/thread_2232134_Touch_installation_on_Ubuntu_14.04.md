---
title: "Touch installation on Ubuntu 14.04"
date: 2014-06-30
forum: General Help
---

### Post by michiel2 on 2014-06-30
Hello, 

For the last few days i've been having problems installing 14.04 on the following hardware :

Intel D525 1.8Ghz 
2GB DDR3 SO-Dimm
ChenMtech Touch Controller : Hardware ID 1bfd/3050 - No known linux drivers.
- The touch controller is shown as 'Touchpack' using lsusb, using Xinput list - it shows as HID TOUCH HID Touch Panel.

Patriot Torqx2 32GB SSD

Did a fresh install and updated everything.

At first i noticed that the touch controller did register 'mouse click' but wasn't able to calibrate is using Xinput Calibrator and adding the 'Calibration' to 10-evdev.conf.
So i started searching and found some things about the touch controller not being in the 'USB_HID' list and being recognized as a 'tablet input'. I was able to read out 'Event1' and 'Event2' in the /dev/input/ dir but forgot how i did that. 

After figuring that out i went to search and found that i could use :

Modprobe -r usbhid
Modprobe usbhid quirks=0x1bfd:0x3050:0x40

By putting that into rc.local (and did chmod -x on that).

Now it does register touch but i can't calibrate it and no matter what i change in either '10-evdev.conf' or adding '99-calibration.conf' it doesn't have any effect - Things i found during my search.
Also when trying to calibrate i have to use my mouse else it will say 'mis click' and won't let me continue.

Then i noticed it suddenly showed 2 touch input devices, using Xinput i tried disabling 1 of them - Xinput disable 13 but that didn't help either.
Using Xinput list i still see 2 input devices, also tried 'blacklisting' it but that didn't do anything either.

After that i tried making a 99-calibration.conf file in /etc/X11/xorg.conf.d/ and putting the snippet from Xinput_calibration in there but no change.

When i use Xinput test 13 or 14 both register input, and it will show a click and coordinates.

Since i'm not that familiar with Linux i have no idea where to find the problem now, i know that it has something to do with not being recognized by Ubuntu as a normal touch controller, but i assumed after the modprobe that would've been fixed.
And since it did register some touch input after the modprobe i assumed it would be easy sailing after that.

Thanks for the help.

---

