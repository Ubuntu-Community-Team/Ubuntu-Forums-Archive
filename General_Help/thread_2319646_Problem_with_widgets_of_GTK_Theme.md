---
title: "Problem with widgets of GTK Theme"
date: 2016-04-06
forum: General Help
---

### Post by Veliko on 2016-04-06
I've been tweaking GTK Theme called "Yosembiance" to my taste. Basically I want to remove the orange accent color and use #9E9EB3 as the accent color.
I've installed TheWidgetFactory and all the widgets of GTK 2 seems to be exactly how I want them. I don't know how to check GTK 3 widgets.
Here is what I did so far:

[LIST]
[*]gksudo gedit Yosembiance/gtk-3.0/gtk-main.css and changed the property of selected_bg_color from orange to #9E9EB3 and save.
[*]gksudo gedit Yosembiance/gtk-3.0/settings.ini and changed the preperty of nselected_bg_color from orange to #9E9EB3 and save.
[*]gksudo gedit Yosembiance/gtk-2.0/gtkrc and changed the property of nselected_bg_color from orange to #9E9EB3 and save.
[*]In Yosembiance/gtk-3.0/assets I changed the pixels of every icon that have orange pixels with #9E9EB3
[*]Reworked some of the icons in Yosembiance/unity
[/LIST]
The Problem
Some of the widgets have combined colors of orange and #9E9EB3. Seems I have to modify some more files, but I don't know which ones.
Any pointers?

---

### Post by Veliko on 2016-04-06
[COLOR=#111111][FONT=Ubuntu]I think I've found the problem I've made a grep search for all the files in theme for the color #f07746 and it's says that in settings.ini and gtkrc the property of seleted_bg_color is #f07746(orange). When I open the files using gksudo gedit it shows that the properties of theselected_bg_color are #9E9EB3. When I try to change again to #9E9EB3 I got errors in the console. 

[IMG]http://i.stack.imgur.com/cnbUg.png[/IMG]Fixed it. Still not working.[/FONT][/COLOR]

---

