---
title: "Accidentally made EVERYTHING transparent."
date: 2008-05-25
forum: General Help
---

### Post by Aesir09 on 2008-05-25
So after my format i decided to install ubuntu in the car on the way to my grandmothers house (&#9835;to grandmothers house we go&#9835;)

anyway all was going well.

and then i decided to configure compiz, using ccsm.
and i was messing around with the "Windows Opacity" if i remember, in the general section

what i was trying to do was change it so that when im dragging the current window, that it has like %70 opacity. 

instead idk why i clicked new, and then enter+enter+enter and i realized that i made everything completely transparent. i got into a shell and removed compiz but when i log on it brings up the splash screen and loads and bam all i can see is my desktop and the few icons on it.

**so basically what i need to know how to do(listed in which i want most):** 
[B]1. Reset compiz settings to default.
2. a command to replace the compiz windows manager, with the gnome default one, _whats the process name so i can_[/B]

```

WTF IS TEH PROCESS LOL --replace

```
**3. completley remove compiz and ccsm**

---

### Post by Forlong on 2008-05-25
Just press [Alt]+[F2] then type ```
metacity --replace
```

To reset your Compiz settings, run this in the terminal:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by Aesir09 on 2008-05-25
thank you so much you were very helpful.

thanked. :)

---

### Post by Forlong on 2008-05-25
No problem, I wish all support requests were as entertaining as yours. :)

---

