---
title: "How do I uninstall fonts?"
date: 2007-12-17
forum: General Help
---

### Post by svivian on 2007-12-17
Specifically, I wich to uninstall "Helvetica [Adobe]" since it's ugly and is used on some web pages instead of my default (and much nicer) Bitstream Vera Sans.

I looked in fonts:/// as per suggestions in other threads but couldn't see it. I also did a system-wide search for it with *sudo find / -name *helvetica** but no luck.

There are also a whole ton of fonts that start with ae_, they're possibly language fonts. They are in fonts:/// - is it safe to delete these straight from the folder or is there a proper way to uninstall them?

---

### Post by svivian on 2007-12-17
bump :)

---

### Post by fragos on 2007-12-17
The simple way is to use synaptic.  Do a search in synaptic for "ttf-" and you'll get of list of font software and the fonts. Mark to uninstal the fonts the don't want and click the apply icon.  After uninstalling the system will rebuild the font cache.

---

### Post by svivian on 2007-12-31
Those all seem like font "packages" to me, which would uninstall several fonts. Really I just want to be able to uninstall the odd font or two. I can't even delete any from fonts:/// (yes, I'm using sudo).

I found one package, ttf-freefont, which mentioned Helvetica, but if I remove it, it will remove "ubuntu-desktop" package.

*Why can't I remove individual fonts?!*

---

### Post by fragos on 2007-12-31
You can sudo delete from /usr/share/fonts/truetype.   when you're done run "sudo fc-cache -fv"

---

### Post by svivian on 2007-12-31
Thanks for the help, fragos. I think I've sorted the issue now. Actually Helvetica wasn't in the "free fonts" package (the description said "similar to Helvetica" so I assumed my system was using it in lieu of said font).

After looking through every folder and file in /usr/share/fonts I finally found it in **/usr/share/fonts/X11/75dpi** and **/usr/share/fonts/X11/100dpi**. My searches hadn't found them because the files had names like helvB08-ISO8859-1.pcf.gz

Anyway I moved them out of that folder and into my home directory as a backup, rebuilt the cache with "sudo fc-cache -fv". If it's useful to anyone, I used:
```
sudo mv -t /home/scott/software/FONTS/100dpi /usr/share/fonts/X11/100dpi/helv*
```
...to move them all at once (there were loads).

---

