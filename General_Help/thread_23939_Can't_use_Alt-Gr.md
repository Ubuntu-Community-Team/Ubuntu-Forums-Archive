---
title: "Can't use Alt-Gr"
date: 2005-04-04
forum: General Help
---

### Post by bigblop on 2005-04-04
I am using a danish keyboard and the FVWM Window Manager. I have run the reconfigure program and chose danish settings whenever I could.

When I press Alt-Gr+2 in this box that I am currently writing in, the browser jumps to "search forums". In an xterm I just get "2" when I press Alt-Gr+2.

Normaly I get AT (the thingie in an emal address) when I press Alt-Gr+2, but this does not work. There is also other things that normaly denpend on Alt-Gr like tilde, pipe backslash etc which I cannot use either.

If I start gnome or KDE instead of FVWM I have no problems typing the Alt-Gr dependant chars.

Hope someone can help because I feel rather crippled when I man not able to send an email.

---

### Post by daniels on 2005-04-04
Edit /etc/X11/xorg.conf, and add the following line in the Keyboard section, right below XkbModel:
Option "XkbOptions" "lv3:lwin_switch"

---

