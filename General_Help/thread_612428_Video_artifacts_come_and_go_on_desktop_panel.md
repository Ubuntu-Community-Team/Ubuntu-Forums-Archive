---
title: "Video artifacts come and go on desktop panel"
date: 2007-11-13
forum: General Help
---

### Post by kansas_plainsman on 2007-11-13
I've got a friend running Gutsy Gibbon on a machine with the Intel 810 video chip set - everything works fine most of the time - but sometimes he is seeing red vertical bars on his desktop panel.  A 'refresh desktop' will usually clear it, but it comes back.  Anyone have an idea what's going on?

---

### Post by kansas_plainsman on 2007-11-22
Well, in the interest of closure - an update.

The Intel 810 chip set 'borrows' regular ram, and that causes recent linux kernels problems (so it appears)

Attempts to use an S3 Virge video card resulted in lock-ups.
Attempts to use a Matrox video card were unsatisfactory as well.

I ended up changing to a motherboard with an Intel 815 chip set and a separate Nvidia GeForce2 MX-400 video card, and using the standard 'nv' driver.  No more artifacts on the desktop.  Problem solved by avoiding the issue all together.

---

