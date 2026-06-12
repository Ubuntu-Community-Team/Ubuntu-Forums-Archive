---
title: "Open Office does not load"
date: 2007-09-24
forum: General Help
---

### Post by 3dmaker on 2007-09-24
OOO does not load, and when i type it into the console it gives me this error
"
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

** (process:9514): WARNING **: Unknown error forking main binary / abnormal early exit ...

"

I think it has something to do with my video card drivers. I have an ATI Xpress 200M running on the Ubuntu "ati" not on the "fglrx"

---

### Post by luisromangz on 2007-09-24
I have the same problem, though it only happens when running XGL (so I can run Compiz in my ATI card).

I'm using the fglrx driver, and when I start a  normal session, without XGL nor Compiz, OpenOffice.org starts successfully. I don't know why, but it seems that OO.org needs hardware acceleration for something.

Maybe you should give the fglrx drivers a try, I use them in the same card as you, and they work quite well. By the way, the version I use is the last version, 8.41.

---

