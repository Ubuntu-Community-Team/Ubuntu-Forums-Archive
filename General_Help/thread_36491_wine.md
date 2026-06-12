---
title: "wine"
date: 2005-05-23
forum: General Help
---

### Post by Infernal on 2005-05-23
hi, 

i installed wine and tested it by installing railroad tycoon II.i simple question, where is the game, i can't find it on my HDD. I installed it in "C:/Program Files" but i can't find that directory.

thx

---

### Post by lakcaj on 2005-05-23
You should have a /home/<username>/.wine directory

It is a hidden directory, since it starts with a .

Within .wine, you likely have a fake_windows directory, or something like that.  If you haven't already, I would install winesetuptk, delete .wine completely, and then run winesetup.  It will try to detect all you hardware and create symbolic links so you can use you CD drives easier, etc, etc. and setup your .wine directory for you.

---

### Post by Infernal on 2005-05-23
thx, found it, but is it possible to run is with the root account???
and how do i run a program, if i do wine <name.exe> it gives an error


thx

---

### Post by alamba on 2006-01-28
infernal were you able to get rtII to work with wine?

Akshay

---

