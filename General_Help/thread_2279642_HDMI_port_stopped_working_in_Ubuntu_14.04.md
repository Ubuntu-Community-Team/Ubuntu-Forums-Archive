---
title: "HDMI port stopped working in Ubuntu 14.04"
date: 2015-05-25
forum: General Help
---

### Post by raspirit on 2015-05-25
Hi. I'm using Ubuntu 14.04. 

My HDMI port in laptop worked fine most of time. Sometimes it stops working but I was able to fix it by some semi-random manipulations like deleting xorg.conf.* files, installing nvidia drivers and removing them, since I'm using nouveau. I had so many issues when tried to use nvidia drivers so I decided to stop use them at all before.

So the case is: my hdmi port worked fine with some cases when it broke but I was able to fix it before. But now I tried all what I did before to make it work without success.

Xrandr output is:

> Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



So it even doesn't see it.

Could anyone help me fix this?

---

### Post by raspirit on 2015-05-26
My laptop hanged and I had to use forced turn off. HDMI started to work again after this. But I'm still wondering why it happens sometimes.

---

