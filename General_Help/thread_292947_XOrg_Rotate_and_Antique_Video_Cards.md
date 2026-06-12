---
title: "XOrg Rotate and Antique Video Cards"
date: 2006-11-04
forum: General Help
---

### Post by Mr. Picklesworth on 2006-11-04
I have recently acquired a rather nice LCD monitor with the ability to go into portrait mode.
It's not a wide-screen monitor, but it would be quite nice, nonetheless.

I found out what seems the easiest way, which is editing XOrg.conf to include the Rotate option for my display driver.
I did that, and now Rotate appears in the screen resolution screen. (And I really hope this is done automatically for most people).

...However, the problem crops up here.

With the i810 driver, my video card (horrible intel integrated thing with an i810 chipset -- don't worry, I do have another decent computer; I'm not completely nuts) does not seem to support Rotate. I looked it up, and this is only supported with i830 and up. Nicely, every piece of software had the foresight to not try it.
Using the alternative driver (is it just called "intel"?!) also does not change matters.

Being one who hates spending money, I am hoping for an easy escape aside from buying a new video card (and, thus, a new motherboard and processor... and RAM and case, since - with the exception of its surprisingly not obsolete Ethernet card and wireless card - this computer is awful).
Therefore, a bunch of questions:

Why do I need to set the Rotate option in the driver settings, anyway?
Can't the window manager keep the video card running at 1280x1024 (as opposed to 1024x1280) and print everything at 90 degrees in the software end of things? I can already get a Gnome panel usable in Portrait mode (drawn vertically), so I wonder why anything else has to be done differently...
Edit: Well, then again, I guess it's rather obvious that software probably wouldn't cooperate very well like that... there may be something, though. (Are old video cards really that daft that they can do 1280x1024 resolution, but not its rotated counterpart?!)

Is it something to do with how the actual drawing stuff has to change for the monitor to be nicely visible in portrait mode? (If so, can I bypass that requirement since mine isn't bad at all like that?)

Perhaps there is some obscure setting in X, or some other piece of software, which I can use to flip things around?


Thanks much in advance!

---

