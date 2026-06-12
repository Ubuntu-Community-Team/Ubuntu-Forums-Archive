---
title: "Configure theme for only gnome-panel (gtkrc)"
date: 2006-11-23
forum: General Help
---

### Post by mucha on 2006-11-23
I'm a bit lost in gtk2-themeing (gtkrc). I just want to configure fg and bg at gnome-panel. Is that possible?

---

### Post by strabes on 2006-11-23
I didn't know there was a foreground and background color...? I just knew there was a main panel color.

One thing you CAN do is change the background image of the panel, which is what I have done. It looks better anyway.

---

### Post by mucha on 2006-11-23
Sorry I didn't explain right. I want to change the textcolor and active background in things like taskbar and plugins. Is that possible?

---

### Post by autocrosser on 2006-11-23
I've dabbled in GTK theme-work over the years & the guide I use (updated regularly;)) is:  [http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)

You will find MORE than enough info there:-D

A "heavy-reading" overview on GTK is: [http://www.gtk.org/~otaylor/gtk/2.0/theme-engines.html](http://www.gtk.org/~otaylor/gtk/2.0/theme-engines.html)

---

### Post by mucha on 2006-11-24
Thanks for the links, but well I'm stuck. 

Should'nt this give any result at all? 

```

style "gnome-panel"
{
  fg[NORMAL]        = "#ffffff"
  fg[PRELIGHT]      = "#ffffff"
  fg[ACTIVE]        = "#ffffff"
  fg[SELECTED]      = "#ffffff"
  fg[INSENSITIVE]   = "#ffffff"

  bg[NORMAL]		= "#ffffff"
  bg[PRELIGHT]		= "#ffffff"
  bg[ACTIVE]		= "#ffffff"
  bg[SELECTED]		= "#ffffff"
  bg[INSENSITIVE]	= "#ffffff"

  base[NORMAL]		= "#ffffff"
  base[PRELIGHT]	= "#ffffff"
  base[ACTIVE]		= "#ffffff"
  base[SELECTED]	= "#ffffff"
  base[INSENSITIVE]	= "#ffffff"

  text[NORMAL]		= "#ffffff"
  text[PRELIGHT]	= "#ffffff"
  text[ACTIVE]		= "#ffffff"
  text[SELECTED]	= "#ffffff"
  text[INSENSITIVE]	= "#ffffff"
}

widget "Gnome-panel.*" style "gnome-panel"
```

---

### Post by autocrosser on 2006-11-24
Hmmm-- I don't know about that--where are you putting it?  What I normally do is create a theme that I can install into /user/share/themes (mainly because I change things about every week or so;))--I'll include one of mine that is REAL blue--I was trying to make all text blue & this works--a bit too much:-?

I'll look into your idea & see if it works (and where it needs to go)--will be this evening or tomorrow (Pacific time)--it's off to work I go:neutral:

---

### Post by mucha on 2006-11-25
Thanks for your help. But the thing is that you make the text blue at everything. I just want to edit gnome-panel :)

---

### Post by autocrosser on 2006-11-25
I was just showing what can be done--I haven't waded thru all the spec info yet--I'll post some info as soon as I've got what I think would work---

---

### Post by mucha on 2006-11-25
Thanks! I can't wait ;)

---

### Post by autocrosser on 2006-11-26
Well-I don't see in a over-view for a way to define only the Gnome-panel via a .gtkrc file--looks like you need to define a system-wide color (kind of like the blue theme)--I'd just start changing values in a "test" theme & do a try & see---I use to remember where there is a theme-tester--I'm sure that I can find it again.....

Edit: In synaptic--gtk-theme-switch--then make a menu item for it--the command is switch2--allows you to preview installed themes without loading them.

---

### Post by autocrosser on 2006-11-26
I have been "looking" around & ran across this tidbit!!

[http://blogs.gnome.org/view/thos/2006/11/20/0](http://blogs.gnome.org/view/thos/2006/11/20/0)

Seems very soon you can have your wish (at least closer to) within the "stock" Gnome theme panel;)

I look forward to it!!

More theme info at:  [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

---

