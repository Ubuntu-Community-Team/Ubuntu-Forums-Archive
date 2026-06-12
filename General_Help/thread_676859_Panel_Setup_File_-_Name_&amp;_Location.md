---
title: "Panel Setup File - Name &amp; Location"
date: 2008-01-24
forum: General Help
---

### Post by drs305 on 2008-01-24
I'm running the standard ubuntu gutsy desktop. I've arranged all my shortcuts on the panel and know my launchers are located in ~/.gnome2/panel2.d/default/launchers

Sometimes the panel gets moved to the side or bottom and the order and all the spacings are lost. What file controls the order and spacing of the launchers on the panel menu? I'd like to backup this file and just restore it when the spacings get messed up rather than reposition them all.

Thanks for any replies.

Just so I can contribute some info as well as receive it:
My top panel is full of shortcuts. When it accidentally gets moved to either side it is very compacted and there is no blank space to right click to select properties and restore its original position. Rather than go into gconf-editor or the menu, I've just put a shortcut on the panel to restore it to the top. The shortcut laucher command is:
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation "top"

Of course, you could have top, bottom, left, or right, depending on your desires, and you could also run this command from terminal.

---

