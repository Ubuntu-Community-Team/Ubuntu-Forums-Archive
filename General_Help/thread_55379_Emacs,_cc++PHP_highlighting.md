---
title: "Emacs, c/c++/PHP highlighting"
date: 2005-08-08
forum: General Help
---

### Post by Paul Bramscher on 2005-08-08
Coming from an RH distro world, I'm used to firing up emacs as a quick-and-dirty PHP editor when I don't need a GUI. I see that the default ubuntu install doesn't have syntax highlighting.

I installed php-mode via synaptic, restarted emacs, and no go. Is there additional work involved to get back my PHP (and c/c++) highlighting? Thanks.

---

### Post by pranith on 2005-09-06
hi there,
I had the similar problem too.
I fixed it like this 
after installing php-mode
open ur .emacs file 
and add these lines


(load-library "php-mode")
(global-font-lock-mode t)

save it and try to open the files I think it should work the way u wanted it to now
bye,
pranith.

---

