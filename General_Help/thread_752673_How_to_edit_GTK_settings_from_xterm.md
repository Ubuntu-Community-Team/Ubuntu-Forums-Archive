---
title: "How to edit GTK settings from xterm?"
date: 2008-04-11
forum: General Help
---

### Post by Baphijmm on 2008-04-11
So recently I've decided to switch over to Fluxbox; I greatly enjoy its versatility and stability over that of Gnome or KDE.  Problem is, for whatever reason, all programs controlled by GTK (Pidgin, xchat, Thunderbird, Firefox, etc.) now have grossly-oversized fonts.  Is there any way to rectify this without the use of the Appearance program?  In other words, is there any way to edit GTK settings from the terminal?

---

### Post by kerry_s on 2008-04-11
create a " .gtkrc-2.0 " file
put->
gtk-font-name = "Sans 14"

adjust font to yours.

my gtkrc->

---

### Post by Baphijmm on 2008-04-11
Or, barring that, another means to fix this problem?

[This screenshot]("http://i2.photobucket.com/albums/y8/Baphijmm/screen.jpg") should better illustrate my problem; the resolution is 1600x1200, and the size of the font of the title bars is what I would like the rest of that text to have, if at all possible.


EDIT: Sorry, your reply must have occurred while I was posting mine.  Where does this file then go?

---

### Post by Baphijmm on 2008-04-11
Thanks, that fixed it entirely.  While I'm looking at this though, is there a way to edit the system colors of GTK?

---

### Post by kerry_s on 2008-04-12
> **Baphijmm said:**
> Thanks, that fixed it entirely.  While I'm looking at this though, is there a way to edit the system colors of GTK?

that would be the theme, usually i would just go into the theme and change what i want. it's the gtkrc file in the theme, make sure you make a backup first.

---

### Post by RedSquirrel on 2008-04-12
> **Baphijmm said:**
> Thanks, that fixed it entirely.  While I'm looking at this though, is there a way to edit the system colors of GTK?

I like to make a per-user copy under ~/.themes. For example:

```

mkdir ~/.themes
cp -r /usr/share/themes/Mist ~/.themes/Mist-custom
vim ~/.themes/Mist-custom/gtk-2.0/gtkrc

```

---

### Post by kerry_s on 2008-04-12
> **RedSquirrel said:**
> I like to make a per-user copy under ~/.themes. For example:

```

mkdir ~/.themes
cp -r /usr/share/themes/Mist ~/.themes/Mist-custom
vim ~/.themes/Mist-custom/gtk-2.0/gtkrc

```

that would work to. :)
unless your a tight wad like me and don't want to spare the extra space for a second copy of a theme.
:lolflag:

---

### Post by RedSquirrel on 2008-04-12
> **kerry_s said:**
> that would work to. :)
unless your a tight wad like me and don't want to spare the extra space for a second copy of a theme.

I'm pretty careful about that sort of thing too, but it's only a few K! :grin:

The main reason I prefer to copy it to ~/.themes is that I can then edit the file without root privileges.

---

### Post by kerry_s on 2008-04-12
thanks RedSquirrel.

---

