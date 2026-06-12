---
title: "[SOLVED] strange colors on the cairo dock"
date: 2008-03-26
forum: General Help
---

### Post by zizzdude on 2008-03-26
hey guys, I installed cairo-dock, and loved it! :D I tried it on one pc and it looked perfect. but when I installed it on my laptop, I get a black colored background over the dock.

[http://bvuong.lv5.org/images/Screenshot.png](http://bvuong.lv5.org/images/Screenshot.png)

is there something I'm missing plugin-wise? or is it something else?

and yes, the linux penguin on my wallpaper is gonna kill windows. :lolflag:

---

### Post by -grubby on 2008-03-26
Do you have a compositor (such as Compiz or xcompmgr) installed?

PS: that's the MSN butterfly, you can't kill Windows if you're aiming for MSN :)

---

### Post by zizzdude on 2008-03-30
yeah, I have both of them, but I still have the black color around the dock.

PS: lol, ok. is there a windows mascot btw?

---

### Post by mcduck on 2008-03-30
> **zizzdude said:**
> yeah, I have both of them, but I still have the black color around the dock.

PS: lol, ok. is there a windows mascot btw?

You also need to run one of them. It doesn't look like you have either one running now..

Try enabling the Desktop Effects (in System/Preferences). That should start Compiz for you.

---

### Post by zizzdude on 2008-03-30
> **mcduck said:**
> You also need to run one of them. It doesn't look like you have either one running now..

Try enabling the Desktop Effects (in System/Preferences). That should start Compiz for you.

some reason, I pressed on the Normal Effects, but it gives me a pop up saying "The Composite extension is not available"

how do I fix this?

---

### Post by mcduck on 2008-03-30
> **zizzdude said:**
> some reason, I pressed on the Normal Effects, but it gives me a pop up saying "The Composite extension is not available"

how do I fix this?

What graphics card do you have? First you need to get full 3d acceleration working with your graphics card, after that enabling desktop effects should work.

If it's an Ati card, and you are using the restricted drivers from Ubuntu repositories you also need to install the xserver-xgl package to enable desktop effects.

As soon as you have desktop effects working Cairo dock, AWN, Screenlets and other applications that need compositing will start working correctly

---

### Post by zizzdude on 2008-04-01
awesome. thanks. :)

---

