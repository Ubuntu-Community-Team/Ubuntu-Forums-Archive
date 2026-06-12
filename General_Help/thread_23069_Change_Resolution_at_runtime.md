---
title: "Change Resolution at runtime?"
date: 2005-03-31
forum: General Help
---

### Post by cwaldbieser on 2005-03-31
Is it possible to change the resolution of my desktop at runtime?  Whenever I try the appropriate option, I get a message telling me that my X Server does not support resizing and rotating the display.  It says I need RANDR 1.1 or greater.  I checked, and I have libxrandr2 v6.8.2-8 installed.  I am not sure how the two relate, exactly.

I have an ATI Radeon 9800 graphics card.  Switching resolutions is not a big deal, as my current resolution is ideal.  However, I did use to be able to do this under Warty.  Anyone have any ideas?

---

### Post by bobmitch on 2005-03-31
I`m assuming you are using the fglrx driver, in which case it`s not possible I`m afraid.  All fglrx resolution changes must be made in your X config file, then restart X.

---

