---
title: "Font Install Help"
date: 2004-10-28
forum: General Help
---

### Post by j_baer on 2004-10-28
I tried to install a font using Nautilus and I get as far as copying the font to the fonts:/// folder and it won't copy.

My guess is I don't have permission as my local user.

Is my only recoarse copy the files from a terminal screen using sudo?

Thanks ....

---

### Post by Rancoras on 2004-10-28
Did you try that?

---

### Post by beesee on 2004-10-29
[QUOTE=linuxbaer]My guess is I don't have permission as my local user.[/QUOTE]
Why do you think this?  Did nautilus or something else give you an error?  The reason I'm saying this is because copying fonts to the fonts:/// location really just installs fonts into ~/.fonts.  And you *should* have write permission in your own home directory.  Did you try running [COLOR=Blue]fc-cache -fv[/COLOR]?

---

### Post by j_baer on 2004-10-29
Thanks for the help ...

I just "sudo copied" them over and ran fc-cache -fv.

---

