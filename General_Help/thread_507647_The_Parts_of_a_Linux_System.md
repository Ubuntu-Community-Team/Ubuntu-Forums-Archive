---
title: "The Parts of a Linux System"
date: 2007-07-23
forum: General Help
---

### Post by ghandi69_ on 2007-07-23
I'm trying to get a better understanding of the different parts of a linux system, and what is all required to get it running, where I have question marks, well, those are my questions...

Lets say I have a server, CLI only install running.  To get things running graphically and to make things more user friendly I need.

Window Manager
Display Manager
Desktop Manager
File Manager
Login Manager

Correct?  and if I did a apt-get install ubuntu-desktop, those would be covered like this...

Window Manager (Gnome)
Display Manager (Xorg)
Desktop Manager (Gnome)
File Manager (Nautilus)
Login Manager(GDM)
Package Manager (Synaptic)

Well, if didn't want all that other stuff that comes with ubuntu desktop, I could start getting those like this..

Window Manager (apt-get fluxbox)
Display Manager (Xorg >> apt-get ??? not sure of the command for this....)
Desktop Manager (???)
File Manager (Thunar/Dolphin)
Login Manager (???)
Package Manager (graphical synaptic??? command line install)

If there are parts of the system I am definitely missing, please let me know.

Thanks for looking at this.

Ghandi

---

### Post by scrooge_74 on 2007-07-23
You can installed xubuntu-desktop which is a lot lighter than standard ubuntu or someother of the window managers like ICE

---

### Post by Seisen on 2007-07-23
For xorg its 
```
x-window-system-core
```

and for package manager you can use aptitude, its takes a little bit of time to get used to.

```
sudo aptitude
```

You really don't need a login manager. You can log in at the terminal and then ```
startx
```

---

### Post by ghandi69_ on 2007-07-23
Thanks for the replies fellas,

Ok, so I have a question regarding the difference between Fluxbox and Gnome.

I keep on hearing that Gnome is a "desktop" manager, or something like that, where as Fluxbox is only a "window manager"

What does this encompass, what are things that Gnome handles that Fluxbox or a window manager does not?

---

### Post by strabes on 2007-07-23
I don't have the answer for your newest question, but you mentioned dolphin as a file manager in your original post. If you're going to use gnome as your WM on your server, you won't want to use a kde/qt-based app because it will have to load all the KDE libs in addition to the gnome ones.

---

