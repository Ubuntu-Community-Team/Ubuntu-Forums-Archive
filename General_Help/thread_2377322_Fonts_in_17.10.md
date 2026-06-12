---
title: "Fonts in 17.10"
date: 2017-11-11
forum: General Help
---

### Post by worik on 2017-11-11
I have just started using 17.10 and I am now tolerating quite ugly fonts in all applications.

I am not familiar with the way fronts are stored and rendered, and when I look at font packages there are bazillions.  Where should I start trying to improve the asthetics of what I see?

I do not even know enough to be able to describe what is irritating me, it just does not look nice

I have attached a screen shot that I hope illustrates my problem

Worik

---

### Post by jbicha on 2017-11-11
Are you using the default Ubuntu or one of the other flavors?

---

### Post by QIII on 2017-11-11
Hello!

Would you please provide another example?  Your image is of the standard Forum font, which we expect to be used on the Forums.

This is not a reflection of the fonts used in Ubuntu in general.

Thanks!

---

### Post by worik on 2017-11-13
I amusing standard UBUNTU 17.10

[http://worik.org/fonts.png](http://worik.org/fonts.png)

---

### Post by nodrog1952iii on 2017-12-09
The freetype2 font rendering changed with 17.10 due to the switch from freetype-2.6.3 to freetype-2.8. The difference in the rendering was caused by the upstream introduction of the TT_CONFIG_OPTION_SUBPIXEL_HINTING parameter in freetype2's /include/freetype/config/ftoptions.h for freetype-2.7.X and later. Its not so much that the font rendering is better or worse but that it is different than before with freetype-2.6.3. This is most noticeable with GTK applications such as Thunderbird and Firefox.

In any event,  the font rendering can be made exactly the same as before by recompiling Ubuntu's version of freetype-2.8 with TT_CONFIG_OPTION_SUBPIXEL_HINTING undefined (commented out).  Subpixel rendering must also be enabled with the FT_CONFIG_OPTION_SUBPIXEL_RENDERING parameter in /include/freetype/config/ftoption.h.

---

