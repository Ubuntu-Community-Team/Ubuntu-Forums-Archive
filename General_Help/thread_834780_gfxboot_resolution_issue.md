---
title: "gfxboot resolution issue"
date: 2008-06-19
forum: General Help
---

### Post by magikasheep on 2008-06-19
i was trying to install gfxboot to make my boot process more pretty, and i somewhat suceeded. it works...but the resolution is wrong and with some themes it gives me a large black box over the theme, and if i press anything, it will go to the bland old default grub look. ive tried a few different themes and they all have this problem. so im wondering if this is a problem with grub picking the wrong resolution, and is there a way to fix this?

unfortunately, i cant find a way to screen shot the boot screen, and i dont have a camera.

edit...by looking at the picture, it looks like the resolution is in 640x480, when it should be in 800x600 i believe. startup manager also says that the boot resolution (i think thats for grub) is 800x600 so, im going to try changeing that, and mesng around with the resolution and see if i can fix it.

ok...i changed the boot resolution settings, and that seemingly did nothing. it looked the same. but i got a closer look at the blackbox that was covering the screen, and it was a list that had two headings at the to rstk and pstk i believe. than it had what looked like a numbered list  
______________
|.rstk.|.pstk.|  something like this, it even looked like it was drawing with dash and underscore charactors. but the list 
|0:.....0:.......|  was bigger, and had some writing after 0: 1: 2: and such. although i didnt get a good look at the 
|1:.....1:.......|  numbering or the writing after.
|2:.....2:.......|
|3:.....3:.......|
--------------

---

### Post by magikasheep on 2008-06-23
any help please? could it be with my graphics card? or did i install it wrong?

---

