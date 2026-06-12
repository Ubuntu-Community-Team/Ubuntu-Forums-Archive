---
title: "Eye of Gnome flashes in full screen"
date: 2007-10-24
forum: General Help
---

### Post by SnowPunk98 on 2007-10-24
If I open an image and make it full screen in Eye of Gnome it goes nuts and starts flashing for some reason. I am using Gutsy, Nvidia restricted, and Compiz.

---

### Post by MozartlovesUbun2 on 2007-11-13
confirm Eye of GNOME 2.20.0 - Gutsy - Full Screen - Blinking - maybe a Bug?

ATI card same here

are there any fixes?

---

### Post by Friedel on 2007-11-15
Same here, ATI too...

Maybe you can try [MIRAGE](http://mirageiv.berlios.de/), it has nearly the same functions. :)

> Mirage aims to be a very simple and easy-to-use image viewer and editor. It provides navigating through lists of images, zooming, slideshow mode, and some simple image manipulations. It also supports more advanced use, like custom actions, but gets out of the way for the user who wants an image viewer, no more, no less.

---

### Post by vasilis34 on 2007-11-22
I have the same problem using nvidia restricted drivers. I 've read a workaround somewhere and it actually works on the specific problem. You have to enable the unredirect fullscreen option on the general options tab of the advanced desktop effects configuration. It works for the image viewer, **BUT** it gives also another problem. There is a weird flicker occasionally in videos played by VLC on fullscreen. It isn't very often and not as annoying as the flicker in image viewer's fullscreen but it seems like the picture loses it's vertical synchronization just for a moment. Anyway if you want, check it and maybe somebody finds a solution to that problem too.

Regards

---

### Post by stocchero on 2007-11-23
Same problem here, intel 945 notebook.
Using gThumb, no problem.
Anyone wtih a solution?

---

### Post by seul on 2007-12-15
> **vasilis34 said:**
>  You have to enable the unredirect fullscreen option on the general options tab of the advanced desktop effects configuration. 
Regards

Thanks for the suggestion, although I actually had to disable it (System &#8594; Preferences &#8594; Advanced Desktop Effects Settings &#8594; General Options &#8594; Tab »General« &#8594; untick »Unredirect Fullscreen Windows«).
But then, maybe that's what you meant, I get a bit confused when it comes to unabling unredirecting by unticking...

---

### Post by vasilis34 on 2007-12-15
XAXA! Yeap it's a bit confusing. 


Have you noticed the flickering on vlc on fullscreen mode? Or have you probably found a solution for this?

Regards

---

### Post by seul on 2007-12-15
> **vasilis34 said:**
> 

Have you noticed the flickering on vlc on fullscreen mode?



Nope. Only in Eye of Gnome; but there it flashed as if it didn't expect a tomorrow.

---

### Post by ceo51378 on 2007-12-17
I have the exact same problem on both my laptop and desktop - both running gutsy.  If you go into your appearance settings and change Visual Effects to 'none' - the problem goes away (but who wants that as a fix?).  At first I thought it was related to the compiz cube but it must be some other setting.

---

### Post by tommyknocker. on 2008-03-18
> **SnowPunk98 said:**
> If I open an image and make it full screen in Eye of Gnome it goes nuts and starts flashing for some reason. I am using Gutsy, Nvidia restricted, and Compiz.

same problem here  :???:
gutsy + nvidia restricted + compiz

no solution yet?

---

### Post by Cann0n on 2008-03-19
I'm using  Radeon Mobility 9100 IGP and I fixed it by unchecking 'Unredirect Fullscreen Window' on the CompizConfig Setting Manager in the System > Preferences > Advanced Desktop Effects Settings > General

---

### Post by tommyknocker. on 2008-03-20
> **Cann0n said:**
> I'm using  Radeon Mobility 9100 IGP and I fixed it by unchecking 'Unredirect Fullscreen Window' on the CompizConfig Setting Manager in the System > Preferences > Advanced Desktop Effects Settings > General

wow!
seems it did the trick!

thank you very much! bye!

---

