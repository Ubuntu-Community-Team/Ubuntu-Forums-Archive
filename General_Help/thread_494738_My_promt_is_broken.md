---
title: "My promt is broken"
date: 2007-07-07
forum: General Help
---

### Post by ztripez on 2007-07-07
I reinstalled my desktop computer and all runs nice.. but all of sudden i realized something had happen to my promt. (Se screenshot). Dosn't matter what user i'm currently using or if i use GNOME or textmode.

Any ideas?

---

### Post by p_quarles on 2007-07-07
That's very strange. Do you have anything installed that might mess with xorg.conf? Like Beryl, Compiz/desktop effects, automatix? Did you have to install a driver to get your video to work?

---

### Post by ztripez on 2007-07-07
> **p_quarles said:**
> That's very strange. Do you have anything installed that might mess with xorg.conf? Like Beryl, Compiz/desktop effects, automatix? Did you have to install a driver to get your video to work?

Ow you thougt i ment the "no borders".
 naah.. i cuted that one out. My problem is the promt. 
the ":~$ pez@Lucy" and with the textmarker in the middle of the text and as I said i get the same error in text mode (tty).

---

### Post by Mr. C. on 2007-07-07
Did you change shells to dash ?

It looks like a bash variable expansion is not being expanded, and this would indicate a different shell is running that does not support that type of variable expansion.

Show the actual setting of the PS1 prompt and indicate the shell you are using.

MrC

---

### Post by p_quarles on 2007-07-07
> **ztripez said:**
> Ow you thougt i ment the "no borders".
 naah.. i cuted that one out. My problem is the promt. 
the ":~$ pez@Lucy" and with the textmarker in the middle of the text and as I said i get the same error in text mode (tty).
No, I understood what the problem was. I asked about changes to xorg.conf because that can often have wide-ranging and strange consequences for how things are organized on your screen.

---

