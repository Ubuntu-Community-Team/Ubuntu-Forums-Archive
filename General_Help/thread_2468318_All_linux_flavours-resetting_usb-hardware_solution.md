---
title: "All linux flavours-resetting usb-hardware solution"
date: 2021-10-25
forum: General Help
---

### Post by vidtek on 2021-10-25
I have been struggling for a while to find a solution to this seemingly insurmountable problem.

[LIST=1]
[*]Live usb distros ALWAYS require an usb stick to be unplugged then plugged back in after a reboot.
[*]They also have an annoying prompt at the end of the reboot process to press enter after removing said usb stick.
[/LIST]

**1)** The hardware solution: an Anker 7port with 3 power only usb3 powered hub. [https://uk.anker.com/products/a7515]("https://uk.anker.com/products/a7515")

I tried in my workshop to see if when the power was removed if the usb hub was reset as though unplugged from the host computer.

It was, the little blue active light went off, the hub was disconnected and I was able to reboot the computer without physically unplugging the usb stick.
 So a work-around, not the most elegant solution, a software approach built-in to the live system would have been far more elegant but this works for my application. I have tested it with a smart plug and even using google assistant voice control I was able to achieve my goal.
The timing is critical, disconnect too early in the reboot process and it will cause the machine to hang (as the usb stick is the current o/s), too late and the bios boot process will already have started.

**2)**  This is courtesy of @sudodus

Edit the grub file where it says "quiet splash"  to "noprompt splash" ---press "E" during the boot menu screen and insert the command.

I hope this is of use to the many others out there who have struggled with this issue, particularly remote administration.

Cheers Tony.

---

