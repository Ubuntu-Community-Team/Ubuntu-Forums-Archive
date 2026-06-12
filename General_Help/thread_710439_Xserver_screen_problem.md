---
title: "Xserver screen problem"
date: 2008-02-28
forum: General Help
---

### Post by danival on 2008-02-28
Hello everyone!

I ran the wubi installation, and everything went fine till the first run, where I got this message from the Xserver:
(EE) VESA(0): No matching modes
Screen(s) found, but none have a useable configuration.
(here: )
[http://wiki.x.org/wiki/FAQErrorMessages#head-83b2f9b8c18db15e641ed9e0be8f9a8364001e5b](http://wiki.x.org/wiki/FAQErrorMessages#head-83b2f9b8c18db15e641ed9e0be8f9a8364001e5b)

I have a Fujitsu/Siemens laptop
AMD Athlon 64 X2 Dual-Core Processor TK-55 1,80 GHz
ATI Radeon Xpress 1200

I've searched my butt off, but can't find exactly the same issue. Tried:
sudo dpkg-reconfigure xserver-org
But get a message telling me xserver is not installed (?)

Any help would be greatly appreciated.

Thanks

---

### Post by ago on 2008-02-28
ctrl+alt+f2
sudo dpkg reconfigure xserver-xorg

---

### Post by danival on 2008-03-03
That made sure I could reconfigure the screen thingy, thanks.

Only problem is, that I haven't got a clue what to select. I've tried a couple different settings: vga, vesa, ati. And then left the rest of the options on default, but still no useable result.

This is what my "device manager" in windows tells me:
Display adapter: ATI Radeon Xpress 1200
Monitors: Generic PnP Monitor

Thank you for your patience with me :)

---

