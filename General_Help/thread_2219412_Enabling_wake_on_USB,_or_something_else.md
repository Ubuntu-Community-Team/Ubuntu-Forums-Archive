---
title: "Enabling wake on USB, or something else"
date: 2014-04-24
forum: General Help
---

### Post by lykwydchykyn on 2014-04-24
I have a Dell Optiplex 755 on which I run Kubuntu 14.04 and connect to my TV.  When it's not in use, I have it suspended.

Currently, the only way to wake it from suspend is to hit the power button, which is obnoxious because the tower is stashed away behind an end table.

What I'd like is some other way to wake it from sleep, such as keyboard or mouse activity.

Most posts I could find say to echo "USBn" (where "n" is the number of the USB port) to /proc/acpi/wakeup to enable wakeup on that port.  I've done this, and when I look at /proc/acpi/wakeup it shows all my USB ports as enabled.

Even so, I cannot wake the device with the keyboard or mouse.

I've tried switching suspend from S1 to S3 in the BIOS, but neither mode makes any difference.  I didn't see any other applicable BIOS options.

Is there something I'm missing?  Anyone have any other ideas for conveniently waking this thing up?

---

