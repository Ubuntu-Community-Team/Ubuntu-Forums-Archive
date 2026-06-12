---
title: "Trouble with swedish letters in terminals."
date: 2005-04-09
forum: General Help
---

### Post by totaln00b on 2005-04-09
Having problems with my swedish letters  (Å Ä Ö ) in terminals ( xterm ) running centericq and Irssi . I can neither type them or see others type them ( they come out very funny looking) . Im using UTF-8 encoding and swedish layout on my keyboard.  Any ideas on what may be wrong ??? 


sorry for the poor english. I blame the hangover..  :wink:

---

### Post by erkki70 on 2005-04-19
Hi,
You might be missing fonts.
Try installing extra xfonts packages from universe repository using Synaptic to see if the problem persists. 

Hope this helps.

Cheers,
Erkki

---

### Post by ttp on 2005-04-19
Gnome-terminal, irssi, UTF-8 and scandinavian letters. It's not good combination. Maybe it's possible to configure with UTF-8, but I swithed to ISO-8859-15 ("sudo dpkg-reconfigure locales"). I'm using finnish language.

---

### Post by totaln00b on 2005-04-19
Tnx ... That did the trick. :)

---

