---
title: "Vinagre closes connection - xvncviewer works"
date: 2008-04-28
forum: General Help
---

### Post by DieKatzeKotzt on 2008-04-28
Hi there,

I have upgraded to the new Ubuntu release Hardy Heron and was just about to check out the new capabilities of Vinagre, when I noticed I could not connect to the VNC-server at my university.

'xvncviewer' however works fine, but I would enjoy using vinagre.
I have searched several bug-reports and discussions but have neither found a solution nor a definite "no way", so I am asking here.

I believe we are using RealVNC server, at least thats what the man page is telling.

best regards, Andre

---

### Post by DieKatzeKotzt on 2008-04-30
Alright - solved
I just forgot that xvncviewer translates the display number into the actual port but with vinagre you will have to add 5900 to it.

Thanks anyway, André

---

