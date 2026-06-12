---
title: "Wierd way to fix Beryl performance issue (opening glxgears)"
date: 2006-10-21
forum: General Help
---

### Post by Moralez on 2006-10-21
Now this is what I call wierd:

- Asus A6Va laptop, ATI mobility x700 256mb PCIE, 1gb ram, etc...

Now, after having a nice grub failure in booting Ubuntu and no being pacient enought to manually fix it I decided to reinstall Ubuntu... I had a 100% stable and fluid XGl + Beryl config...

Now I have...

- Perfect recent ATI drivers install;
- Perfect (well, it seemed like it) Beryl install;
- Ubuntu completly up-to-date...

And now my Beryl is sluggish.. slow and choppy...

Exept... -> alt+f2 -> xterm -> glxgears

That's right... opening glxgears malkes Beryl fast and nice...

Now what? I have to open glxgears everytime I boot? Honestly.. I don't care, does anyw know how to fix this or, at least, make glxgears boot in a "hidden whindow" or something like that?

Thanks.

---

### Post by Druid Healer on 2006-10-21
System -> Preferences -> Sessions -> Startup Programs -> Add -> glxgears
This is for gnome.

---

