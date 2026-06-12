---
title: "GTK_THEME= doesn't work for gnome-terminal?"
date: 2016-05-09
forum: General Help
---

### Post by vasa1 on 2016-05-09
If I just want to see what a gtk3 app looks like with a theme other than my default, I can run:
GTK_THEME=Adwaita mousepad
or
GTK_THEME=Ambiance mousepad
or
GTK_THEME=Greybird mousepad

Other gtk3 apps behave the same way but if I try the same approach with *gnome-terminal*, it still opens with my default gtk3 theme, the one I point to in my *~/.config/gtk-3.0/settings.ini*. Does this happen to anyone else? 

16.04 Lubuntu Openbox session, fully updated. (Please note that *GTK_THEME=theme_name app_name* requires 3.12+. It won't work with 14.04 which has 3.10.)

Edit: It seems that *not all* applications respond to *GTK_THEME=*: [http://worldofgnome.org/running-gtk-applications-different-themes-per-app/](http://worldofgnome.org/running-gtk-applications-different-themes-per-app/). Maybe gnome-terminal is one of them.

---

