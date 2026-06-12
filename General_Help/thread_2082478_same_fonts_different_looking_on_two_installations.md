---
title: "same fonts different looking on two installations"
date: 2012-11-09
forum: General Help
---

### Post by legendbb on 2012-11-09
Same fonts, same size: DejaVu Sans Mono

On two different installation of same distributions (Ubuntu 10.10)
Two machine has identical system appearance settings (checked carefully)

Look very different. (distance between letters, thickness, please see attachment)

Font difference is almost everywhere in gnome.

Why is that?

Please share your knowledge,

---

### Post by timgood on 2012-11-09
Are both machines using the same graphics drivers? Do they have the same graphics hardware?

---

### Post by ajgreeny on 2012-11-09
And are you sure you have exactly the same settings for font rendering/smoothing, and the same dpi resolution in both machines?

---

### Post by legendbb on 2012-11-09
I am 100% sure they have identical DPI and rendering settings. But yes, they have different Graphic cards.

Thanks for your comments,

---

### Post by Rebelli0us on 2012-11-09
Under Appearance Preferences > Fonts > Subpixel Smoothing > Hinting options can make HUGE difference in the look of fonts.

Video card type can make a difference too, but not as much as subpixel smoothing.

---

### Post by legendbb on 2012-11-12
Hi all, I found my problem. Sorry for all the misleading descriptions.

The newly install Ubuntu doesn't have Dejavu Sans Mono installed (for some reason). So on this machine system just used something to replace Dejavu Sans Mono (ugly one).

Another machine had ttf-dejavu package install at some point I totally forgot.

Font ubuntu font install: [http://ubuntuforums.org/showthread.php?t=275202](http://ubuntuforums.org/showthread.php?t=275202)

---

### Post by dcstar on 2012-11-14
> **legendbb said:**
> Hi all, I found my problem.


Then MARK the thread!

---

