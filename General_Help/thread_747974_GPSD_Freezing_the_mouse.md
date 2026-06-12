---
title: "GPSD Freezing the mouse"
date: 2008-04-07
forum: General Help
---

### Post by dchurch24 on 2008-04-07
Hi all,

I have a USB GPS unit (BU-303) which seems to work - I haven't actually got it working with any software yet (I think because the unit is indoors, but on a windowsill it can't see enough sats to triliterate the signal) but have managed to get some output via:

sudo gpsd -N -n -D 2 /dev/ttyUSB0

...so I know it's all working,

The thing is, when I run that, or try to use Roadmap, or GPSDrive etc... the mouse pointer disappears.

I assume that this is some sort of USB 'conflict' but I'm not sure where to start looking to resolve it.

When I kill the GPSD process the mouse pointer becomes visible again.

Any pointers would be very much appreciated.

---

### Post by dchurch on 2008-04-07
Nope - nothing I do stops this from happening.

---

### Post by dchurch on 2008-04-08
Please? ;-)

Someone must have a clue - I really don't want to have to use my Laptop (winxp) to do this - I tried installing the drivers for the USB device yesterday - after 4 hours I gave up! This is why I like Ubuntu!

---

