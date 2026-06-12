---
title: "icons missing after installation if icon theme"
date: 2017-12-05
forum: General Help
---

### Post by severin-kunz on 2017-12-05
I've installed Arc Icon Theme and Arc Theme

[https://github.com/horst3180/arc-icon-theme](https://github.com/horst3180/arc-icon-theme)

However, now some icons are completely missing from all themes. For example Terminal and Gedit.

This sounds like a silly problem, but maybe there's an easy solution. Don't want to reinstall Ubuntu again.

Thanks

---

### Post by Dennis N on 2017-12-05
According to information on the linked page, that theme doesn't include any application icons:

> This theme doesn't provide application icons, it needs another icon theme to inherit them. By default this theme will look for the Moka icon theme to get the missing icons. If Moka is not installed it will use the Gnome icon theme as fallback. To change the application icons, edit Arc/index.theme and replace Moka with the name of your preferred icon theme

---

### Post by severin-kunz on 2017-12-05
Alright, but that shouldn't mean that those icons are completely missing now should it?

Thanks for your reply

---

### Post by Dennis N on 2017-12-05
I tried the theme in Ubuntu 17.10 and don't see any application (or any other) icons missing (Overview > Show all applications). In particular, text editor and terminal look like gnome icon theme and Ubuntu Software is from hicolor icon theme. See screenshot attached.

Check the index.theme file. First three lines here show:

```
[Icon Theme]
Name=Arc
Inherits=Moka,Adwaita,gnome,hicolor
Comment=Arc Icon theme


```
gnome, Adwaita, hicolor icon themes are installed by default in Ubuntu 17.10. Should be on your system?

---

