---
title: "Lubuntu 18.04.3: cannot lower sceen resolution"
date: 2019-10-04
forum: General Help
---

### Post by stilnovo1 on 2019-10-04
[COLOR=#242729][FONT=Arial]Hi to Everybody,

I've just bought a new HP laptop 15-dw0004nl. I actually have a dual boot, Windows 10 and Lubuntu 18.04.3.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]In 'monitor settings' there is only the FHD resolution as available, I cannot change it to a lower resolution (most comfortable for me). 

The output of xrandr gives also only that resolution:`[/FONT][/COLOR]

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
eDP-1-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     60.06*+  40.04

[COLOR=#242729][FONT=Arial]I've tried both drivers, Nouveau and Nvidia, it doesn't change the problem.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What could I do?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks in advance![/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Andrea[/FONT][/COLOR]

---

### Post by CatKiller on 2019-10-04
Using the display at a non-native resolution is a really bad plan.

Instead, you should be looking at the build-in settings for interface scaling and changing the size of text and icons.

---

### Post by stilnovo1 on 2019-10-05
Thanks for the reply! Why is not a good idea? In the other computers that I manage, I am able to choose different screen resolutions since they are proposed in 'monitor settings' or at least I can change them in the configuration file. But here xrandr gives only that available resolution, isn't it strange? Consider that open box is not so... flexible

---

### Post by CatKiller on 2019-10-05
> **stilnovo1 said:**
> Thanks for the reply! Why is not a good idea?  

Because flat panel displays have a fixed number of pixels. 

Setting the resolution lower instead of scaling the screen elements is a hangover from CRTs, which had an optimal resolution but not a native one. Doing the same on a flat panel display just gives you a blurry mess. 

> In the other computers that I manage, I am able to choose different screen resolutions since they are proposed in 'monitor settings' or at least I can change them in the configuration file. But here xrandr gives only that available resolution, isn't it strange? 

Not really. xrandr displays the resolutions that the display reports that it can do. The display saying that it can only use its native resolution is an acceptable behaviour. 

> Consider that open box is not so... flexible

You can change the text and icon sizes in the places that you normally change text and icon sizes. You can set system-wide scaling for Qt or GTK applications with [the appropriate environment variables](https://forum.lxqt.org/t/detailed-guide-to-enable-high-dpi-scaling-on-lxqt/507).

---

### Post by stilnovo1 on 2019-10-05
Thank you very much for your clear explanation! It was a doubt I've always had, I mark as 'solved'.

---

