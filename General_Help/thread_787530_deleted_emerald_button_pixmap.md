---
title: "deleted emerald button pixmap"
date: 2008-05-09
forum: General Help
---

### Post by fizikz on 2008-05-09
I was in the Emerald Theme Manager in the Themes Settings tab, under Edit Themes -> Buttons, and it seems that the "clear" button actually deletes the pixmap for the corresponding button type. Now there is no image for the Close button on any window when I use Emerald. How/where can I get the buttons.close.png pixmap?

---

### Post by can8dnSix on 2008-05-09
I did the same thing; to fix it, I 

```
sudo apt-get remove emerald
```

then

```
sudo apt-get install emerald 
```

:) 

I hope that helps you but I learned the same thing as you.

lyw

---

### Post by fizikz on 2008-05-09
I tried that and the pixmap is still missing :P 
I also tried reinstalling any other components of compiz fusion I could think of, but still nothing.

---

### Post by can8dnSix on 2008-05-09
Go into your home directory, after you do a removal of emerald and delete .emerald from your home directory. Then re-install emerald; that should get you back up. The missing icons are in .emerald/themes

---

### Post by fizikz on 2008-05-09
Thanks a bunch, that worked!

---

### Post by AldenIsZen on 2009-01-06
Yes it did work, thanks! I wish I knew how to thank you in this forum, but I haven't figured it out yet.

---

