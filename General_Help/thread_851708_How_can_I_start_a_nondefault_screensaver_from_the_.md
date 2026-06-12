---
title: "How can I start a nondefault screensaver from the command line?"
date: 2008-07-06
forum: General Help
---

### Post by BryanFRitt on 2008-07-06
How can I start a specific non-default screensaver(random, blank, etc...) from the command line?

I know how to start the default screensaver, but I would like to be able to start a specific screensaver that isn't the default.

-

related commands that I've tried:

Starts the bank screen in a window (How can it be set to run like a normal screensaver?)
*/usr/bin/kblankscrn.kss *

Starts the default screensaver and locks it (How can it be set to run a non-default screensaver?)
*dcop kdesktop KScreensaverIface lock &> /dev/null*

Starts the 3D time screensaver one in a window (How can it be set to run like a normal screensaver?)
*/usr/lib/xscreensaver/t3d *

Starts the barcode one using a 24 hour clock in the desktop (How can it be set to run like a normal screensaver?) (it makes the icons sort of hidden)
*/usr/lib/xscreensaver/barcode -clock24 -root*

-

Now, how can I start custom(not default) screensaver(as a screensaver, not a window) from the konsole window? (random, blank, clock, other, etc...)

---

