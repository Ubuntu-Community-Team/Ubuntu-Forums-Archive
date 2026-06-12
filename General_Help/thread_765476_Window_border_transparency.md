---
title: "Window border transparency"
date: 2008-04-24
forum: General Help
---

### Post by omns on 2008-04-24
Where in compiz can I control the transparency of my window borders?

---

### Post by kk0sse54 on 2008-04-24
If you are using an emerald theme just go into the emerald theme manager click on the theme you want and press the tab edit Themes and under Frame Engine select the oxygen engine then save the theme and you should have transparent window borders

---

### Post by omns on 2008-04-24
> **C!oud said:**
> If you are using an emerald theme just go into the emerald theme manager click on the theme you want and press the tab edit Themes and under Frame Engine select the oxygen engine then save the theme and you should have transparent window borders

Is it possible in metacity as well? The out of focus windows are transparent by default. Can I adjust the in-focus windows as well?

---

### Post by kk0sse54 on 2008-04-24
I personally don't know of a way using metacity but no doubt there probably is. Try searching for and downloading a metacity theme that has clear window borders from GNOME-look.org or a KDE site if your using kubuntu.

---

### Post by neatojones on 2008-04-24
Alt-F2
-> gconf-editor

apps-> gwd -> metacity_theme_active_opacity

You can play around with the other settings under gwd also to get the effect you want.  The reason why emerald is preferred is because when you increase the transparency of the metacity this way, it makes the title and buttons transparent as well, while this doesn't happen in emerald.

---

### Post by omns on 2008-04-24
Thanks all :)

---

### Post by omns on 2008-04-24
> **neatojones said:**
> Alt-F2
-> gconf-editor

apps-> gwd -> metacity_theme_active_opacity

You can play around with the other settings under gwd also to get the effect you want.  The reason why emerald is preferred is because when you increase the transparency of the metacity this way, it makes the title and buttons transparent as well, while this doesn't happen in emerald.

Actually, this effect suits the theme I'm using at the moment. 

Thanks again :)

---

### Post by mttza1 on 2010-11-22
> **neatojones said:**
> Alt-F2
-> gconf-editor

apps-> gwd -> metacity_theme_active_opacity

You can play around with the other settings under gwd also to get the effect you want.  The reason why emerald is preferred is because when you increase the transparency of the metacity this way, it makes the title and buttons transparent as well, while this doesn't happen in emerald.

This can also be manipulated in $HOME/.gconf/apps/gwd/%conf.xml and i believe /usr/share/gconf/defaults/10_compiz-gnome

does anyone know of a way to set windows to be transparent, unless there maximised?

---

