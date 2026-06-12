---
title: "Ugly font rendering in firefox in xubuntu?"
date: 2006-12-02
forum: General Help
---

### Post by strabes on 2006-12-02
Title pretty much says it all. I installed xubuntu-desktop to check it out and the font rendering in firefox in it is really really ugly. It's hard to explain. Any ideas? Font rendering in everything else in xfce and gnome is great btw.

---

### Post by IcemanV9 on 2006-12-02
Maybe if you could install msttcorefonts (M$ fonts)? It should help a lot.

---

### Post by grumpymole on 2006-12-02
Alex,

Try Edit -> Preferences -> Advanced under Fonts & Colors.  Then change the fonts to Bitstream Vera Sans or Serif.  This should improve them.

Also, the size of the Firefox menu fonts sometimes doesn't match the size of the system fonts.  There is a fix [here]("http://grumpymole.blogspot.com/2006/10/fix-for-firefox-chrome-fonts-not.html").

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by capital on 2007-02-19
The problem is with Firefox, not the system.  Here is the easiest fix:

type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' (zero) -- this forces firefox to use system font settings
restart firefox

No need to mess with other configuration files.
That was for Firefox 2.0 and up.

For Firefox 1.5, just go to Preferences > Content > Fonts & Colors
Go to the advanced dialog box, and tell it to use system font settings.

---

