---
title: "Switch between GPU ports"
date: 2014-03-15
forum: General Help
---

### Post by christian16 on 2014-03-15
Hello!

I'm totally new to Ubuntu, but I decided to install it along with Windows 7.
Installation went fine and I have done the usual repository updates as soon as the system finished installing Ubuntu 13.10.
However, I've had my HDMI monitor plugged in to the Motherboard through a DVI adapter, because the screen would not appear on the HDMI port on either my Motherboard or my HDMI port on my AMD R9 290x.
If I plug the monitor into the HDMI port of the 290x, which is what I want my screen to be shown on Linux (and it works just fine on Windows) it just shows the default Linux wallpaper, with no start menu or mouse or anything. It just sits there. I have to plug it in back to the DVI port on the Motherboard.
I tried looking for the flgrx drivers on Additional Drivers, but the list comes blank. Even if I wanted to install AMD driver from the site, I would have to have the monitor plugged into the Graphics Card, right? How can I resolve this issue?
Any help would be greatly appreciated!
Thank you for your time.

---

### Post by 3rdalbum on 2014-03-15
That card is too new for Ubuntu 13.10 to immediately recognise and offer a proprietary driver for, but you can download said driver from the AMD website.

You might be able to find a PPA for that driver, which is basically a server that Ubuntu can use to install the driver and keep it up to date. Try searching Google for "fglrx ppa" and see what you find.

You can install the driver and then reboot and plug the monitor into the card. With the driver installed it should work as expected.

---

### Post by christian16 on 2014-03-15
Thank you! Will try that out.

---

