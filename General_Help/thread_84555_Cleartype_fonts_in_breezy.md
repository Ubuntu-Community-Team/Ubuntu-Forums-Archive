---
title: "Cleartype fonts in breezy?"
date: 2005-10-31
forum: General Help
---

### Post by brugca on 2005-10-31
In hoary, cleartype fonts worked very well, nevertheless, now I have installed breezy, and sometimes the letters become blurred, and the programs takes more time for loading.

(I don't speak english well, sorry)

Thanks!

---

### Post by suRoot on 2005-10-31
Cleartype looks fine on my thinkpad.

Have you tried System -> Preferences -> Font & tweaked the settings under "Details"?

Also, what kind of video card do you have?

---

### Post by RSX311 on 2005-10-31
[http://www.paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/](http://www.paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/)

Scroll down to "Making Ubuntu More User Friendly" and follow the directions,  It made my fonts look 100 times better.

---

### Post by brugca on 2005-11-12
Solved! Thanks!

My configuration of xorg.conf caused this error... in concrete this line:

Option "RendelAccel" "true"

Caution! :) Bye!

---

### Post by mechanic on 2005-11-13
Why do people talk so loosely about 'cleartype' fonts. Cleartype is Microsoft technology, and one area where they just got it right. Ubuntu lacks the cleartype tuning tool that makes it so easy to set up Windows with superior font rendering.

m.

---

