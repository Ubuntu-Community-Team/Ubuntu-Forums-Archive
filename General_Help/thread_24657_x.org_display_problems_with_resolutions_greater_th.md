---
title: "x.org display problems with resolutions greater than 1024"
date: 2005-04-07
forum: General Help
---

### Post by ivanwillsau on 2005-04-07
Hi

I have just moved from XFree86 to x.org and I can not set correctly the display to any thing other 1024x768 (smaller or greater). I have a IBM laptop (R50p) with an ATI Mobility FireGL T2 graphics card. The native resolution of the laptop screen is 1600x1024 but when I choose that setting (or anything other than 1024x768) I get lots of vertical lines down the right side and at the bottom of the screen. Everything worked OK with XFree86 is there any way to get it working again, should I go back to XFree86? 

Any idears whould be appreciated.

Thanks
Ivan

---

### Post by poofyhairguy on 2005-04-08
[QUOTE=ivanwillsau]Hi

I have just moved from XFree86 to x.org and I can not set correctly the display to any thing other 1024x768 (smaller or greater). I have a IBM laptop (R50p) with an ATI Mobility FireGL T2 graphics card. The native resolution of the laptop screen is 1600x1024 but when I choose that setting (or anything other than 1024x768) I get lots of vertical lines down the right side and at the bottom of the screen. Everything worked OK with XFree86 is there any way to get it working again, should I go back to XFree86? 

Any idears whould be appreciated.

Thanks
Ivan[/QUOTE]

Post you xorg.conf please.

---

### Post by ivanwillsau on 2005-04-08
I think that I have attache the xorg.conf file (this is the first time I have tried)

---

### Post by ivanwillsau on 2005-04-08
Second time lucky with the xorg.conf file

---

### Post by kermy on 2005-04-08
You should add the resolution to the modes in the xorg.conf. the modes lines should read
[INDENT]modes   "1600x1200" "1024x768" "800x600" "640x480"[/INDENT]
or whatever modes you'd like. You can also remove all the sections that are not 24 bit.

---

### Post by ivanwillsau on 2005-04-08
My problem is not the modes I can change to all the different resulutions but I cannot get any mode other than 1024x786 (that includes higher and lower resolutions) to work with out strange lines down the side and at the bottom.

---

### Post by kermy on 2005-04-09
Well, you state that the native resolution of your R50p is 1600x1024, but the resolution of my R50p is 1600x1200 so that could be the problem. The vertical lines could be because of scaling effect. The other resolutions may also not be wel proportioned.

---

### Post by ivanwillsau on 2005-04-09
Sorry typing too many resolutions the resolution is 1600x1200 not 1600x1024. I have tried other resolutions before and the screen does handle them well, both in Ubuntu and windows. So I am certain that the problem is not choosing the wrong resolution. I have seen this problem in the past when I was choosing other distributions to use with this laptop and on older desktop computers. It was this issue that made the dicession easy to go to Ubuntu very easy.

---

