---
title: "Hardy Heron via Wubi 8.04 Display problem on new Tosh Latop"
date: 2008-04-25
forum: General Help
---

### Post by oserdavid on 2008-04-25
Sorry for double-posting - but I didn't realise this forum existed.

Hardy Heron via Wubi mostly doesn't work for me. Display didn't come in as it should during install (gray screen, moving shadows, resolving to almost black with the odd horizontal whiteish line or two). But I waited for the disk to stop thrashing, then did hard close. Switched on. Chose Ubuntu instead of Vista - came in fine!!

Logged in, checked for updates (none), opened Firefox, imported my bookmarks from another partition/disk. Found the Windows network printer. All hunky-dory. Turned off, via Ubuntu,

Later, after restart, selected Ubuntu again: no display - same symptoms as during install. Heard drumbeat. So typed in name, waited, typed in password. But nothing. No possibility of software-based switch-off this time. Also found it difficult to hard-switch off. Eventually succeeded (with the dreaded disk screech you don't want to hear). Tried a few more times - same lack of display issue.

So far it's worked once (immediately after failing during install) and failed a further 3 times. I think I caught a flash of error message about failure to connect to somethingorother bus at one point when switching off.

It's a new Toshiba Satellite Pro P200 Intel Core 2 Duo T5550 (latest BIOS) with 17" WXGA+ screen, running Windows Vista Business SP1, Wubi is installed into the otherwise empty F partition of one of the two hard disks (configured as C and F). The other partition is D, which seems to be on the other physical disk.

I've uninstalled Wubi and Ubuntu for the time being, and now I'm going to run a chkdsk. But I'd like to try again, if someone has an idea what went wrong (and, as an aside, why is the iso image from install marked 'AMD64'. I'm running an Intel machine - has that got anything to do with it, perchance?)
David

---

### Post by ago on 2008-04-25
[https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3](https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3)

---

### Post by oserdavid on 2008-04-25
Many thanks - but that says:
"If such issues manifest before Linux-side installation (after first reboot but before second reboot), press "esc" at boot after selecting Ubuntu. Select "Safe graphics mode".
If you experience problems after installation, press "Ctrl+Alt+F1" and run:
sudo dpkg-reconfigure xserver-xorg
Select the Vesa driver and leave all other options at default. Then reboot. That will allow you to boot into a safe graphic mode (limited resolution) you should then be able to install the appropriate drivers or try other solutions as appropriate"

Do I take that to mean - on booting into Ubuntu do esc then choose 'safe graphics mode' then when in Ubuntu, run "sudo dpkg-reconfigure xserver-xorg" and select Vesa driver. Then reboot. And my problem should be resolved? Or I should then be able to install "appropriate drivers"? If the former - great! If the latter ????
David

---

### Post by oserdavid on 2008-04-26
> **ago said:**
> [https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3](https://wiki.ubuntu.com/WubiGuide#head-e3a360bb3c91f569b4ab6f2d5a25521420e55bf3)

ago - You might also want to include the following link for folks with an ATI Mobility Radeon HD 2600 display adapter...

[http://www.cyberarmy.net/library/article/1777](http://www.cyberarmy.net/library/article/1777)

Me, I think I'll wait till I have a few hours to spare.

What's puzzling me, though, is why it worked just the once without me having to bother my head about such things....
David

This, from Ubuntu forums may also be helpful to those with the time and patience:

[http://ubuntuforums.org/showthread.php?t=570391](http://ubuntuforums.org/showthread.php?t=570391)

Bottom line is - anyone with an ATI Mobility Radeon HD 2600 display adapter - which is very common nowadays - is likely to encounter severe difficulties installing and running Ubuntu, whether via Wubi or any other means. It's still an OS for enthusiasts and fiddlers, not mainstream.

---

