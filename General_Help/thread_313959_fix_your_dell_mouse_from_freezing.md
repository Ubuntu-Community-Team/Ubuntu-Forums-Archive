---
title: "fix your dell mouse from freezing"
date: 2006-12-06
forum: General Help
---

### Post by airzer0 on 2006-12-06
hi well i recently bought a dell dimension c521, for a great bargin. however when i installed ubuntu 6.06 my mouse pointer would freeze after a few min. the only way to fix the issue was to un plug it and plug it back in. So i went searching,looking and reading and found that a lot, and i mean a lot of people were having the same issues. seems that is you try any flavor of linux you will get the same mouse keyboard freezes. So after reading in the dell fourms of all places for a couple of days i ran across this solution. Seems that the usb and the onboard nic card go through the same irq say irq5. so what i did was disabled the onboard nic and replaced the pci modem with a pci nic card. i have a dell dimension c521 amd 64 running 6.06 dapper. its been three days now and not once has my mouse frozen again

---

### Post by magicfab on 2007-01-24
e521n desktops also had the same issue which was solved by updating to the latest BIOS upgrade from Dell. Can you confirm this would work on you PC ? also see:
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries)

---

### Post by omshanti on 2008-07-21
I tried updating to the latest BIOS but was unable to -- I seem to be stuck at 1.0.0. I followed the instructions here:

[http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx](http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx)

but it told me that no updates were available. More specifically:

[INDENT]Searching storage directory for available BIOS updates...
Checking System BIOS for Dimension C521 - 1.0.0
	Did not find a newer package to install that meets all installation checks.

This system does not appear to have any updates available.
No action necessary.[/INDENT]

I'm running Hardy Heron, a fresh install, on a Dimension C521. I tried following these instructions:

[http://ubuntuforums.org/showthread.php?t=475100](http://ubuntuforums.org/showthread.php?t=475100)

but my system ID (0x01EC) is not on the list linked from there.

I downloaded the BIOS update from Dell itself, but it's a .EXE file; Tried running it with WINE, and got a big ol' error dump that I can't make anything useful out of.

I'm running out of clue and out of patience. Anyone up to helping? I'll be all grateful!

---

