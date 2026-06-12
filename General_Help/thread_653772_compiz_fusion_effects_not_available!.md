---
title: "compiz fusion effects not available!"
date: 2007-12-30
forum: General Help
---

### Post by Jedi007 on 2007-12-30
Okay in my last format I got this error Composite something could not be enabled.. something like that at least. Anyway I solved it by installing a certain package in synaptic, the thing is I completely forgot what it was called ! I did install my restricted driver (which is in use) and compizconfig manager.

This time I got the same error except I used an alternate solution where I go in xorg and change a the composite value to 1, but then even though that error leaves I get a new one when I enable try to enable effects:

"Desktop effects could not be enabled"

I really want my old solution back! does anyone know which package I'm talking about?

thanks!

---

### Post by erfahren on 2007-12-30
including your video card make in your post would've helped.

anyway, if you have an ATI card you're thinking of "xserver-xgl"

(if that's the case the Composite Extension needs to stay disabled.)

---

