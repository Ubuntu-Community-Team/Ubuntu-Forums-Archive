---
title: "Font not working very well"
date: 2007-11-02
forum: General Help
---

### Post by morelite on 2007-11-02
I installed a font with apt-get.  I figure my entire system would recognize it with no problem.  Well, it does, but not totally.

The installed fonts shows up in xfontsel.  Fonts can be displayed within programs.

But for some reason, programs like Openbox would not recognize it.  The title part and menu of Openbox shows another font than I specified.

When apt-get installed the font, it put them all in /usr/share/fonts/X11/misc.  It gave me a "warning: /usr/lib/X11/fonts/misc does nto exist or is not a directory."  I do not know what that means.  There is no /usr/lib/X11/fonts(/misc) by default.

I have already added /usr/share/fonts/X11/misc to my /etc/X11/xorg.conf.

What else is there that I need to do to get the installed font to work?

---

