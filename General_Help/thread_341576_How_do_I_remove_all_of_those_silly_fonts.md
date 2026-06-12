---
title: "How do I remove all of those silly fonts"
date: 2007-01-18
forum: General Help
---

### Post by Athanasius on 2007-01-18
I really dislike many of the fonts that come with Ubuntu.  How do I remove the ones that I do not want.  What would be the necessary fonts that I would need to retain?

---

### Post by mssever on 2007-01-19
You can remove the font packages that contain the fonts you don't want, or:

Go to /usr/share/fonts and hunt through the mess of subdirectories for fonts you don't want, then delete them (or, you might want to move them to a temporary holding location in case you make a mistake). When you're finished, run ```
sudo fc-cache -fv
``` and the fonts are gone. You might want to log out or even reboot to be 100% sure.

I wouldn't advise removing any of the standard fonts, unless you want things to look really ugly. In particular, keep sans, serif, and anything with deja vu in its name. Also, if you have the Microsoft core fonts (arial, times,tahoma, verdana, etc.), you'll probably want to keep those, as most web pages rely on them.

---

### Post by Athanasius on 2007-01-24
Thanks

---

