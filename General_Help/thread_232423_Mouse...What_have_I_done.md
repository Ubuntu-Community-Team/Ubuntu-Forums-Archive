---
title: "Mouse...What have I done?"
date: 2006-08-08
forum: General Help
---

### Post by hatman on 2006-08-08
I was playing about trying to add something and ended up knackering X Server, so much so that it wouldn't start.  After booting into another OS I came across a solution in these forums (cheers for that!) using dpkg-reconfigure but now my mouse wont work correctly, cant find anything anywhere pointing to what I need to change.  The right click has gone, when it's clicked it enlarges the screen, similarly when I scroll the wheel up, scroll the wheel down and it's fine.  I suspect it's some setting in the reconfigure that I've changed but am at a loss to figure out which one...If it helps, it's a Microsoft USB Mouse plugged into a USB/PS2 converter and it's been working fine up until earlier...

EDIT: Just found out that if I hold the third click (wheel) I can get back the right click and scroll up...

---

### Post by Ocxic on 2006-08-08
try running "sudo dpkg-reconfigure xserver-xorg"
(do "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak" first to save your current config, to restore your origonal config reverse the files places) this will allow you to reconfigure everything about your monitor, vidcard, keyboard and mouse.

If your not sure what to select you can press enter to accept the default setting.
The only advise i give you is unless your absolutly sure of the settings, use "simple" to select your monitor size. (it will ask simple, medieum, advanced as the options.)

PS: That X11 spoken as X-eleven

---

### Post by hatman on 2006-08-10
thanks for that, I've done it and it's still the same... :(

Curiously enough, when my daughter logs in on her account, the mouse is working fine with no problems like I have.  Obviously it's a setting somewhere, checked my xorg.conf and her xorg.conf and they are identical... anyone any ideas where I can look next?

---

