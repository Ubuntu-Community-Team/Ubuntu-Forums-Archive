---
title: "Anti-aliasing in firefox 3"
date: 2008-06-16
forum: General Help
---

### Post by Excalibre on 2008-06-16
Several betas ago, I tried out Firefox 3 but was displeased that, for whatever reason, subpixel anti-aliasing didn't work, making it rather unpleasant to look at. My understanding is it needs to be compiled with some sort of library or something but this is beyond my abilities to deal with. Is it likely that there will be a package in the repositories that fixes this, or alternatively does anyone know how I'd go about doing it myself?

---

### Post by Pjotr123 on 2008-06-16
Subpixel rendering is a thing of the window manager, not of Firefox. It works fine on my machines. This is how I did it:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 3 )

---

### Post by Excalibre on 2008-06-16
> **Pjotr123 said:**
> Subpixel rendering is a thing of the window manager, not of Firefox. It works fine on my machines. This is how I did it:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 3 )

Uh, no. Maybe they fixed this issue since Beta 2 (I couldn't find anything that said so but maybe I didn't look hard enough.) Anyway, at that time at least a lot of people noticed that Firefox 3 on Ubuntu did not handle subpixel smoothing properly, making pages look godawful, while Firefox 2 did. I understand that there's a setting in Gnome to turn it on, the problem being that Firefox 3 was still not smoothing fonts.

---

