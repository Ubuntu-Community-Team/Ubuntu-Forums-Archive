---
title: "Displaying 2nd Desktop [ctrl] + [alt] + F3"
date: 2008-01-21
forum: General Help
---

### Post by mikeym on 2008-01-21
Hi,

I'm wondering what the feasibility of having a separate desktop display for running games under wine. Since I can't do anything whilst I'm in wine on my desktop I was wondering if it was possible to have a separate one maybe accessed through [ctrl] + [alt] + F3 or something. 

Would this be possible and if it is could I still run things like compiz and the xfce panel on the other desktop?

Thanks for your thoughts,

Mikey

---

### Post by cdenley on 2008-01-21
You can have two X sessions running simultaneously, but I don't think you can have 2 gnome sessions running as the same user. I tried doing something like this with ATI's fglrx driver, and it didn't work, so you might want to try with the vesa driver first. You should read "man xinit" if you want to try this.

---

