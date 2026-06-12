---
title: "Insane graphical glitches"
date: 2013-01-25
forum: General Help
---

### Post by Gaffgarion on 2013-01-25
Hello there. Just finished installing lubuntu 12.04, I like it, but randomly some weird graphical glitch appears - icons and other things disappear, and my mouse cursor becomes a messed up square of pixels.
Screenshots attached. Red squares on second screenshot aren't glitches, just there are some photos of mine :p But the rest is a one big glitch.

I've tried to install fglrx - it didn't work, the graphical mode stopped working, and I was left on-by-one with tty1 :D

Tried to install Gallium drivers - nope, the glitch is still present. Tried to change subpixel rendering of font - nope, doesn't work.

Also, while installing, I accidentally deleted PQSERVICE partition - can it be the reason(but I think no)? Because before deleting I used Ubuntu and everything worked fine.

My graphic card is  ATI RS690M [Radeon X1200 Series].


So, any suggestions?

---

### Post by windscape on 2013-01-25
Hi,

Look [here]("http://ubuntuforums.org/showthread.php?t=1989543") for details describing the same issue being resolved by booting with the nomodeset kernel command line option.

For details on how to do that, look [here]("http://ubuntuforums.org/showthread.php?t=1743535").

---

### Post by Gaffgarion on 2013-01-25
Hm, I'll try that.

And now I tried to reinstall the fglrx. Now it works, but the resolution is awkward and the system says there's no graphical adapter :(
What to do?

---

