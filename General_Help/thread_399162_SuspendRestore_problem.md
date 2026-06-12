---
title: "Suspend/Restore problem"
date: 2007-04-02
forum: General Help
---

### Post by vladk2k on 2007-04-02
Hello.
I keep bumping into a problem that I've had with edgy and now feisty beta. I cannot seem to be able to restore susccessfully from standby. The computer starts up, the HDD starts working, but nothing is happening.
Once, only once I was able to catch a glimpse of something. There were 4 or five of tose lines with
```
* something bla bla    [ OK ]
```
and then, the screen cleared and tow more lines with something like "USB cannot ..." (it was less than a second displayed, and then the screen went blank).
Now, there are two issues that might affect this:
1 - current USB devices:
OnBoard Soundcard (C-Media CM6501B) is connected on the USB  bus
Keyboard & Mouse Receiver is connected on USB
(not connected at that time) USB headphones
2 - Strange options in the BIOS config that might affect the suspend/resume operation
Repost Video when resuming from STR - Enabled
USB OHCI fast restor from STR - Disabled (was enabled when I caught that glimpse, now that it is disabled I don't see that any more, it just stays blank)
ACPI HPET Table - Enabled (default setting)

Thing is, under Windows XP I've always been able to suspend/resume without a problem.

Below is my Hardware configuration, in case it helps:
AMD Athlon64 3200+ @ 2100MHz (FSB 210MHz x 10 Multiplier)
Asrock 939Dual-VSTA Motherboard (ULi M1695 chipset)
2x 512MB RAM TwinMOS value, PC3200 (400MHz DDR)
GeForce FX 5700 (that is the card which I used, I now have a 7600GT but haven't tried suspend/resume yet)
OnBoard SATA disabled (not used)
Maxtor 160GB P-ATA HDD (IDE 1 Master)
LG 4163B DVD-Writer (IDE 2 Master)
LG CD-Writer (IDE 2 Slave)
OnBoard NIC is not used but is enabled (ULi PCI Fast Ethernet Adapter)
Realtek 8139-based NIC
And the peripherals are all connected via USB, I listed them above.

So, questions will be:
1. How can I, after restarting from the button, see what error messages there were at the previous session?
2. How much hardware should I remove, in order to test what is causing the hang. I **could** try booting with all onboard hardware disablet, unplug everything from USB (switch my keyboard+mouse on PS/2), but iyou can imagine that means I have to cripple my system just for it to work.
3. How well is suspend/resume supposed to work, comparing to Windows? Has it always been a problem? Because if it has and never has been "fixed", that's it, I might as well abandon and only suspend when I am in Windows.

---

