---
title: "Emacs gone wild!"
date: 2007-04-05
forum: General Help
---

### Post by Thunk on 2007-04-05
My Emacs decided to play tricks on me. Since installing some new fonts on my 6.10 it only shows squares instead of normal characters.  I tried re-installing emacs, renaming my .emacs and removing the newly installed fonts.  I also installed a couple more things since the last successful run of Emacs so many things could have done that.

Any ideas?

---

### Post by spin2cool on 2007-04-06
check your xorg.conf file.   Make sure the font paths are correct:

There's a known issue where they moved the fonts in Edgy, so some programs that edit/generate your xorg.conf change it

They should look like this:
"/usr/share/X11/fonts/misc"

NOT like thisL
"/usr/share/fonts/X11/misc"

(fonts and X11 are reversed)

---

### Post by Thunk on 2007-04-07
Worked like magic!

Cheers!

---

