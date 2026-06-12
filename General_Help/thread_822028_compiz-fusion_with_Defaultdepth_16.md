---
title: "compiz-fusion with Defaultdepth 16 ?"
date: 2008-06-07
forum: General Help
---

### Post by Gaougalos on 2008-06-07
Is it possible?
With Nvidia drivers 173.14.05

---

### Post by Forlong on 2008-06-08
Care to elaborate why you want that in the first place?

---

### Post by Gaougalos on 2008-06-08
more fps :)

---

### Post by Forlong on 2008-06-09
Well... that's most probably possible but not without problems on a Nvidia card.
You can check by adding this to your **Section "Screen"**```

	DefaultDepth     16
```
If it's already there, change 24 to 16

Then restart X and try it out.


Usually, this will result in no window boarders.

---

### Post by Gaougalos on 2008-06-09
Yes, i know how to change it, but as you said i have no window boarders.
I want to know if there is a tip to have both. And default depth 16 and window boarders. With compiz.
With ati on my laptop i do it. But with Nvidia i can't.
Does anybody know how?

---

### Post by Forlong on 2008-06-09
You have to ask that the developers of the nvidia driver.

---

