---
title: "wine and HiSuite + huawei phone via usb."
date: 2020-01-18
forum: General Help
---

### Post by dwater on 2020-01-18
I'm trying to get Huawei's HiSuite running. It's designed for Microsoft Windows, so I'm running it in Wine. It seems to run ok, but won't 'connect' to my phone, which is plugged in via USB.

I notice that my phone works fine with nautilus, etc, so I know it is connected to Ubuntu ok. Adb works as usual. I wonder what the relationship is between 'hdb' and 'adb' - the naming surely isn't coincidental - the instructions say to give permission on the phone for 'HiSuite' to use 'hdb'....

Is there some trick to getting USB working with apps in Wine?

Any other things I need to be looking at?

Ubuntu 19.10
Huawei Mate 30 Pro

---

### Post by CelticWarrior on 2020-01-19
It won't work with Wine. Similar apps don't work either, BTW. Nothing that requires interaction with hardware peripherals at that level is expected to work with Wine or any kind of emulation.

If you really need it - you don't - you may try with a Windows virtual machine. Or install Windows in dual-boot.

---

### Post by dwater on 2020-01-19
> **CelticWarrior said:**
> It won't work with Wine. Similar apps don't work either, BTW. Nothing that requires interaction with hardware peripherals at that level is expected to work with Wine or any kind of emulation.

If you really need it - you don't - you may try with a Windows virtual machine. Or install Windows in dual-boot.

Ok, thanks. I haven't needed it yet, but I was curious what it was about...I'm not interested in getting Windows. I have a Mac mini (or two) lying around somewhere, so that would be the option I'd go for, but I can't be arsed with that. If I have them out for something else, perhaps (I only have them for debugging web apps on Safari anyway :/).

---

