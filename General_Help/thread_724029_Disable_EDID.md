---
title: "Disable EDID"
date: 2008-03-14
forum: General Help
---

### Post by posterberg on 2008-03-14
I've got a Radeon 9800 PRO card that won't detect my TFT, using DVI, properly.

I've tried using:
OPTION "NoDDC" "True"
OPTION "IgnoreEDID" "True"

To override whatever faulty data the driver receives from the screen.

The logs does however indicate that the driver totally ignores those options.

Are there any other way to tell the driver to not detect monitor settings.

I know that my manual modelines are ok, they do at least work if I switch to the ati driver, still using DVI. They do also work if I use fglrx with a VGA cable.

fglrx version is 8.45.4

/p

---

### Post by kesman on 2008-03-14
Maybe you could try the latest fglrx, you can install it easily with Envy, google for it.

---

### Post by posterberg on 2008-03-14
Updated but no luck...

I am still stuck with 1024x768 on a monitor that can do 1600x1200...

---

