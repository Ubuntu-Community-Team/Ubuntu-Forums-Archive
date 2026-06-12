---
title: "Composite extension: not present."
date: 2008-04-29
forum: General Help
---

### Post by darkwoofe on 2008-04-29
I get this error every time I try to run compiz.

I'm using an  ATI Radeon Xpress Series card (1150, I think). Can someone please help me out?

---

### Post by sujoy on 2008-04-29
see if you have this section in your xorg.conf

> 
Section "Extensions"
Option "Composite" "Enable"
EndSection 

---

### Post by darkwoofe on 2008-04-29
Nope, that isn't in there. Where should I add it, or will adding it to the end do?

---

### Post by darkwoofe on 2008-04-29
I added it to the end and it fixed my problem for me. Thank you so much! I didn't think I'd ever get this fixed! I really appreciate the help.

---

### Post by sujoy on 2008-04-29
My pleasure. :)

---

