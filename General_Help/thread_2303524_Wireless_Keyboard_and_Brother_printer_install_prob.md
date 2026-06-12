---
title: "Wireless Keyboard and Brother printer install problems &amp; solutions."
date: 2015-11-19
forum: General Help
---

### Post by kurt18947 on 2015-11-19
This is not a request for support but rather a couple issues to be aware of so mods, please edit/move/delete as you see fit.

First was with a Logitech keyboard/trackball combo. K350 keyboard, M570 trackball both using one of the unifying receivers. I was finding keystrokes not appearing on the screen for several seconds after pressing the key(s). They'd appear all at once and one or more characters would be missing. I'd read of keyboard glitches with gnome and am using gnome-shell so didn't think a lot of it. Logging out/logging in usually fixed the problem. I thought perhaps there was something going on with resume/suspend as the problem seemed to appear after a resume, not from a fresh boot.  Then the trackball started misbehaving as well.  I wonder if the problem was low batteries so removed the batteries, check and reinserted them. Both devices started behaving as expected when the batteries were removed/reinserted without log out/log on.  I've since started cycling the devices' respective power switches when they misbehave.  I don't know if I have an unreliable receiver or some interaction between the devices, Ubuntu-Gnome and the motherboard (Gigabyte MA785US2H). If a wireless keyboard starts buffering keystrokes for several seconds, try recycling the power.

The second issue was with installing a Brother printer on Ubuntu Mate 15.10.  I've used Brother's installer script with great success but for some reason the script would run, the printer would appear to install, a print job would be sent and the log said the print jobs had completed. There was no ink and paper though. It turns out the repository I was using apparently was missing some packages that the Brother installer needed. I uninstalled, changed repositories and updated then reinstalled.  The printer functioned as I'd become accustomed to. I'd run into a missing package with this repository     (bloomu.edu) a week ago when installing VirtualBox on another machine so I guess I should have thought of that possibility sooner.  I hope this will help some of you chasing problems where the usual fixes don't work.

---

