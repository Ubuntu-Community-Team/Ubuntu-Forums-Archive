---
title: "Ubuntu 15.10 stuck"
date: 2015-12-10
forum: General Help
---

### Post by Johnny_D._Wicked on 2015-12-10
I have one issue with ubuntu 15.10 and that is every time I try to shut down the laptop, I get stuck at the ubuntu purple screen logo with message saying: reboot shutdown now.... or something like that. 

I waited and left the laptop alone because I thought it would turn off eventually but 4 hours later checking back on it, it's still stuck on that screen. I had to hold the power button to actually turn it off.

I tried clicking the power icon at the corner in ubuntu and choosing shutting off and also thru the terminal with sudo but the result of stuck screen is the same. Rebooting doesn't seem to having a problem though just shutting down.

I read in a few places online and people are saying it's a common bug in ubuntu 15.04 and 15.10 version. Is that right? Anyone else having this problem and does anyone know of any fix? I wanted to use Linux Mint 17.2 or 17.3 but my killer 1525 wifi card or wacom have problems with it thus I went with ubuntu 15.10 as my hardware worked after update but this stuck shutdown screen is bothering me. Any help?

---

### Post by Johnny_D._Wicked on 2015-12-11
Bump

---

### Post by SirMoo on 2015-12-11
I've noticed the same... :/ I'm getting stuck on reboots and shut downs very often. It just never seems to want to finish. It's not every time, but more than half...

---

### Post by howefield on 2015-12-11
Try shutting down in verbose mode, which might give you some clues as to where it gets stuck by removing "quiet splash" from the grub boot line.

A few suggestions in [this thread]("http://ubuntuforums.org/showthread.php?t=2217602&page=2") that might be worth reading.

---

### Post by Johnny_D._Wicked on 2015-12-11
Tried editing the grub and removing the quiet splash and added the acpi trick to it...still same problems. :(

---

### Post by Johnny_D._Wicked on 2015-12-12
In the meantime until this ubuntu 15.10 shutdown hang is fixed I have to shutdown and hold down the power button on the laptop or have to reboot into windows (i dual boot) welcome screen and shut down from there...sigh -_-

---

