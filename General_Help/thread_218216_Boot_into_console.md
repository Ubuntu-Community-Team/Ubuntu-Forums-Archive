---
title: "Boot into console?"
date: 2006-07-18
forum: General Help
---

### Post by Unknowndeepness on 2006-07-18
Hello there again.
Sorry for asking many dumb questions ^.^

Anyway, before i was in ubuntu, i had SuSE, and then i could edit some file somewhere to get it to boot into console, and make an ".xinitrc" in my homefolder and start whatever with startx.

How can i do this in ubuntu?

Thanx for your help! :)

---

### Post by geco on 2006-07-18
you must delete the link /etc/rc2.d/S99gdm (or S99kdm if you use KDE) 
in this way you will boot in text mode ;)

---

