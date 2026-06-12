---
title: "Black windows"
date: 2007-09-03
forum: General Help
---

### Post by blue4paper on 2007-09-03
Sometimes when i open a window, it goes completely black. So i always have to resize it to a much smaller size for it to become clear. Is this because of my graphics card or wine? Because even when I'm not running wine, it still goes black.

---

### Post by ddrichardson on 2007-09-04
Are you running Beryl? If so this is a known issue that hasn't been addressed yet related to video memory not being released.

---

### Post by blue4paper on 2007-09-04
yeah I'm running beryl, except for the time i had beryl it never happened until i installed wine.

---

### Post by ddrichardson on 2007-09-04
The bug is known as "black screen of death" there are a few workarounds if you check google - there's one [here]("http://blog.ifitcangowrong.com/open-source/linux/ubuntu/beryl-remove-the-black-screen-of-death").

---

### Post by Steveway on 2007-09-04
It's a bug in Nvidia's drivers.
More precise in their implementation of GLX_ext_texture_from_pixmap.
Nvidia has to fix it, there are workarounds but they either slow it down or decrease functionality.

---

### Post by astralsin on 2007-09-04
try clicking the "Indirect Rendering" option in the beryl menu

---

### Post by siralphred on 2007-09-04
what if you are running compiz fusion? is there a workaround for that too?

---

