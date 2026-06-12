---
title: "Eeepc 1025c Graphics Driver Issue w/ Lubuntu--Fails on Boot"
date: 2013-06-16
forum: General Help
---

### Post by Sequoia Bird on 2013-06-16
Hello,

I recently installed Lubuntu on my Asus Eepc 1025c. It's SO much faster, and I can keep it this way too. However, it's not perfect. The brightness is not adjustable. When I boot, after I type the first password (below the Lubuntu logo, after the Asus screen goes away), the screen is a random colored pattern. See pic below. The computer is unresponsive, except the little square can be moved by the mouse, and the brightness adjust keys work! 

 [ATTACH=CONFIG]243876[/ATTACH]

After I hold the power button to shut it off, I can turn it on again and it works as it should (save the brightness adjust). It works fine until it powers off and I have to turn it on again.

I'm pretty sure it's a graphics card driver issue. I understand cedarview graphics drivers are not available for raring/13.04. Perhaps there's a way to fix it without going back to precise?

Thanks for your help!

---

### Post by cincinnatus13 on 2013-06-16
[https://edzeame.wordpress.com/2012/11/21/ubuntu-12-04-3600-gma-driver-for-intel-cedarview/](https://edzeame.wordpress.com/2012/11/21/ubuntu-12-04-3600-gma-driver-for-intel-cedarview/)

Not saying this will solve it (it is 12.04 documentation) but it's worth a shot. Otherwise, reset your X session.
Ctrl+Alt+F1 at the login screen, drop to root, sh /etc/X11/Xreset

---

### Post by Sequoia Bird on 2013-06-16
[FONT=arial][COLOR=#000000]cincinnatus13--Thank you so much! The first thing worked! I'm not sure I actually got the cedarview driver (my knowledge of the graphics drivers is a haze... do I have an older version or another, more generic driver?) because the apt-get update commands always returned lines about missing files. The brightness was adjustable once I edited[/COLOR][/FONT][COLOR=#000000][FONT=Lucida Grande][FONT=arial] /etc/default/grub though, and now it starts up like it should! [/FONT]
[/FONT][/COLOR]

---

