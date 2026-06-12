---
title: "ttyUSB?  name change after suspend/resume, symbolic link for usb device"
date: 2014-04-24
forum: General Help
---

### Post by martin18 on 2014-04-24
Hi

Absolute Beginner here, kindly bear with me....

I have Ubuntu 13.04 installed on older (Core2Duo) media center style x86 hardware.

A case-integrated IR receiver is attached to an internal USB header. The device shows up in /dev/ttyUSB0 after booting. The IR server software receiving the IR commands requires this as an input parameter.

After I suspend the machine and resume the /dev/ttyUSB0 is no longer there but an /dev/ttyUSB1 has been created. If I suspend and resume again it reverts back to USB0. The result is that the IR server is unable to receive any IR commands as it is bound to the no longer existing ttyUSB.

I would be grateful for help with 2 questions that I was unable to find answers to even after extensive search in the forums.

1. Is the behavior of changing the tty name after suspend resume a standard Ubuntu behavior? Can this behavior be changed so that the tty name does not change with every suspend/resume?

2. If the behavior is correct and there is no way to force the ttyUSB name to be the same before and after suspend then there seems to be the possibility to create a symlink and place a rule to that effect into the local rules folder. I have seen a few examples of creating symlinks for GSM modems but have not yet been successful in creating a symlink for my device. Any pointers or examples would be greatly appreciated.

Many thanks

Martin

---

