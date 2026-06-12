---
title: "FGLRX on FujitsuSiemens 5110 FA DVI"
date: 2008-03-11
forum: General Help
---

### Post by posterberg on 2008-03-11
I've just changed from using a VGA cable to a DVI one. I am running fglrx version 8.45.5.

My monitor is a FujitsuSiemens 5110 FA and it seems that the fglrx driver can't read the monitor specification properly. The read data seems cut off in some way. This makes the fglrx driver believe that my monitor is only capable of 1024x768, while it worked perfectly in 1600x1200 using my VGA cable.

The resolution works perfectly with DVI if I just change the driver name to ati instead of fglrx so I figure everything else in my xorg.conf is setup correctly.

Is there any way to override the EDID data? I've tried putting in the following options in my driver section.

OPTION "NoDDC" "True"
OPTION "IgnoreEDID" "True"
(have tried yes, no, true, false, 1, 0 in various combinations)

The Xorg.log tells me that the driver ignores those options for some reason, have they maybe become obselete?

Would be nice if it was possible to complete tell the driver to don't bother asking the monitor anything since I know that my modelines etc are perfect.

Advices are very welcome!


Oh, btw the card is a radeon 9800 pro, running up to date Gutsy

---

