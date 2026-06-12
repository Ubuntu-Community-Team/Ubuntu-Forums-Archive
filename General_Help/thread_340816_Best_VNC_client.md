---
title: "Best VNC client?"
date: 2007-01-17
forum: General Help
---

### Post by Kethinov on 2007-01-17
For some reason, whenever I use xvncviewer to view a computer with a resolution larger than mine, the scrollbars will scroll right and down, but not left and up. Meaning, I end up stuck in the bottom-right corner eventually and have to close the window and reconnect to get back up to the top left.

This VNC client isn't so great anyway... are there any others anyone would recommend?

---

### Post by oracle5 on 2007-01-17
I had that same problem so I switched to Krdc and it works perfectly and is prettier looking too.

oracle5

---

### Post by scorp123 on 2007-12-28
> **Kethinov said:**
>  I end up stuck in the bottom-right corner eventually and have to close the window and reconnect to get back up to the top left. Use the right mouse button :lolflag:

That version of the vnc client that you used is following some ancient UNIX-ish X/Windows designs, and the left mouse button will only scroll you down and right, the right mouse button will only scroll up and left. To scroll freely you'd have to use the middle button. There are some other programs (which these days nobody uses anymore it seems) that function this way. :)

You might want to try "krdc" or "tsclient" ... both are far more 'modern' clients that will work as one would expect these days. :)

---

