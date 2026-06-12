---
title: "bootable custom Linux ISO to USB"
date: 2017-04-17
forum: General Help
---

### Post by andrea87 on 2017-04-17
Hi,

Would like to either copy the ISO to a USB stick to be able to boot from it to load a Linux custom image

Or else copy an already working (with both BIOS and UEFI) bootable USB with the same Linux to another USB drive.

I tried the dd command but seems that it is missing some required files as says something like Operating System not found when trying to boot from it.

do pen drive brands matter and when using dd should I point it to sdc or sdc1?, Should I partition the destination USB drive or just format as FAT?

I want it to work both on BIOS and UEFI, do you have any suggestions?

---

### Post by ian-weisser on 2017-04-17
Did you include a bootloader in your custom iso?

---

### Post by yancek on 2017-04-17
You would have to post some details on how you actually created the iso if you expect help.  If you use the dd command, it is to the device not a partition so in your example; /dev/sdc

---

### Post by C.S.Cameron on 2017-04-17
Mkusb is a good tool to do as you ask.
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by andrea87 on 2017-04-17
found the custom iso ready, I know that it is working on a USB drive (booting on both BIOS and UEFI) so need to duplicate it to another USB drive or else re-image a USB drive by using the iso file.

I expected the dd command to work in either cases, but again have seen different implementations of the same command, some included the sync, others the file size 1M or 4M etc...

Does dd copy the bootloader since the created USB drives are not becoming bootable?

---

### Post by ian-weisser on 2017-04-18
dd is a low-level copying program, used mostly by wrapper scripts and applications instead of by the user directly.
It copies exactly what you tell it to copy. No more, no less. That's why it needs complex scripts and applications (like mkusb) to tell dd what to copy.
dd is also variously known as 'disk destroyer' and 'data destroyer' for the same reason.

We gently suggest you use a more friendly tool (like mkusb and similar applications) that will thoughtfully include bootloaders for you.

---

