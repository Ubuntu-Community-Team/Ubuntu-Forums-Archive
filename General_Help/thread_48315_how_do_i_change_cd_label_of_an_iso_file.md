---
title: "how do i change cd label of an iso file?"
date: 2005-07-12
forum: General Help
---

### Post by brickbat on 2005-07-12
hi, I have an iso file but the cd label inside the iso is wrong.  How can I change it please?

thanks
bb

---

### Post by emmet on 2005-07-12
I thought "there has to be something, somewhere" - but no! 

I have just two recommendations: the first is burn the .iso to a CD - or mount the .iso directly and then create a new .iso with mkisofs from the original (changing the volume name as you go - the command is in the mkisofs man page).

..or use non-GPL like [isobuster](http://www.smart-projects.net/isobuster/) which is meant to run OK in Linux under wine.

I think I'd go for the first option....

Emmet

---

### Post by brickbat on 2005-07-14
um...why can't i mount it and then use mkisofs to create a new one.  Isn't there a kind of isobuilding program?

---

### Post by emmet on 2005-07-14
Have you tried mounting the .iso and creating a new one with mkisofs?

Emmet

---

