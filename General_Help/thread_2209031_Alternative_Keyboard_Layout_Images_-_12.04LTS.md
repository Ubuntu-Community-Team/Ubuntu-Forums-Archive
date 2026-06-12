---
title: "Alternative Keyboard Layout Images - 12.04LTS"
date: 2014-03-03
forum: General Help
---

### Post by 2CV67 on 2014-03-03
We sometimes have to type with an alternative (Spanish) keyboard, so I tried to get that to work.
Logically, you just have to add it in All Settings > Keyboard Layout.
But that does not work.
You also have to modify a file - /etc/default/keyboard
XKBLAYOUT="fr" > XKBLAYOUT="fr,es" in our case (normal keyboard is French).
Then it works (after reboot).

Now the problem is the on-screen layout chart.
This is a fixed-size window, which takes up most of the screen on a netbook!
Even then, it is practically useless, as the useful information is squeezed into a small space...

As an aside, Windows 7 does this job much better...

Anyway, I would like to try modifying the image.
But first I need to find it.

Can anybody tell me where it might be?

Or has anybody already found a good solution?

Thanks!

---

### Post by 2CV67 on 2014-03-12
Bump!

Nobody know where this image is located in the file system?

I found a copy of the better W7 image & used Gimp to whittle it down even smaller (without number pad, special-function keys etc > 433x117 pixels).
But when I open that image with any viewer, it opens with wasted space above & below.
Seemingly image viewers don't adapt to low-wide images?

Second question: Does anybody know how to get a low-wide image on screen without wasted space?
Preferable without even window headers etc.

Third question: Is there any way to get such an image to be always visible, on top of an active document?

Thanks for any tips!

---

