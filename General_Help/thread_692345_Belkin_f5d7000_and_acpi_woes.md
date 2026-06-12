---
title: "Belkin f5d7000 and acpi woes"
date: 2008-02-09
forum: General Help
---

### Post by cdaaawg on 2008-02-09
I have a working Ubuntu 7.10 installation to which I would like to add a Belkin Wireless G Desktop Card model # f5d7000 ver. 5000. Prior to adding the card, the system functions well. After the card is installed and the system powered up, the boot process freezes just after this boot message:

Starting up . . .
[0.000000] ACPI: DMI BIOS year = 0, assuming ACPI-capable machine

I then power down by holding for 5 seconds and releasing the front panel power button. I power up and esc to the grub boot menu, edit the kernel command line to add 
acpi=off and the system then boots and runs like a top until I shutdown - at which point the system hangs somewhere in the power down process. I guess this is normal since acpi support has been turned off via the grub boot option acpi=off, except for the fact that I don't get any message saying that it is safe to turn off the computer. The Belkin card works well in Windows, so I'm sure it is not a hardware problem. Ubuntu again works just fine when the card is removed. Any help with this issue would be appreciated. I am comfortable using terminal commands and scripts if you need any system info. Thank you.

---

