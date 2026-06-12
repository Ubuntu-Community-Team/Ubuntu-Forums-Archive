---
title: "Active tab color in Geany 1.23.1"
date: 2013-10-29
forum: General Help
---

### Post by vasa1 on 2013-10-29
I'm using **Geany 1.23.1** from the software center and Lubuntu 13.10.

I would like to know how the appearance of tabs in Geany is determined.

I've looked at **/usr/share/geany/geany.gtkrc** but couldn't figure out whether anything in that file helps. (*I could change certain things like the text color of a tab in which changes have been made but not yet saved.*) 

I also looked at the various **gtk2** themes I have in **/usr/share/themes**: some themes do a better job of differentiating the background color of active and inactive tabs but the one I liked best is the way **Clearlooks** does it. The Clearlooks theme has just one relevant file, **/usr/share/themes/Clearlooks/gtk-2.0/gtkrc**. But I couldn't see how the blue bar is applied to the active tab.

Is that somehow coded into the Clearlooks engine and not controllable from within Clearlook's **gtkrc**? If it is a feature specific to the Clearlooks engine, then I'll have to figure out something else because I don't want to have Clearlooks as my theme: there's no gtk-3 support.

---

### Post by vasa1 on 2013-10-29
Well, I haven't found how to get the blue line on top of the tab but I found code that lets me increase the contrast of the active/inactive tabs. In my current theme, Numix, which is part of "shimmer-themes" from the software center, I need to modify ~/.themes/MyNumix/gtk-2.0/gtkrc as follows.

Original:```
# Notebook

style "murrine-notebook-bg" {
	bg[NORMAL] = @base_color
	bg[ACTIVE] = shade (0.87, @base_color)
}

```Modified:```
# Notebook

style "murrine-notebook-bg" {
	bg[NORMAL] = shade (1.2, @base_color)
	bg[ACTIVE] = shade (0.9, @base_color)
}

```

---

