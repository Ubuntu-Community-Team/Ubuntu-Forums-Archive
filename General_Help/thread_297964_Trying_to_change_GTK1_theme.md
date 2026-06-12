---
title: "Trying to change GTK1 theme"
date: 2006-11-12
forum: General Help
---

### Post by wb8976 on 2006-11-12
I want to change the GTK1 theme to something nicer since XMMS menus look ugly and the font is too big. So, I downloaded gtk_theme_switch from the software repository. But whenever I try to change a theme with it, It doesn't change. I ran it from a terminal and tried changing it from there, and this is the message I get when I hit apply:

```
Gtk-CRITICAL **: file gtkentry.c: line 440 (gtk_entry_set_text): assertion `text != NULL' failed.
```

Same error appears when ran under superuser.

Anyone know what this error means and how I can change the gtk1 theme?

---

### Post by Bil-E-daKid on 2006-11-24
Yep - me too.  Not getting the same error but gtk-theme-switch does not appear to be changing the default font for GTK1 apps (audacity, pptpconfig, xmms etc etc) even though it does seem to be changing the ~/.gtkrc file.

Any ideas anyone?

---

### Post by Bil-E-daKid on 2006-11-24
Hey - found an answer.  Make a .gtkrc.mine file in your home folder and put this in it:

> include "/usr/share/themes/Default/gtk/gtkrc"
style "default-text" {
fontset ="-bitstream-bitstream vera sans-medium-r-normal-*-*-90-*-*-p-*-iso10646-1"
}
class "GtkWidget" style "default-text"

Then run this from a terminal window:

> echo "include \"$HOME/.gtkrc.mine\"" > ~/.gtkrc-1.2-gnome2

Your gtk1 apps should look much nicer now ( but still not like GTK2 apps because that's just not gonna happen!)

---

### Post by CatKiller on 2006-11-24
You might find this useful, although I've never tried it:

[HOWTO: Gtk1.2 not so ugly]("http://ubuntuforums.org/showthread.php?t=107135")

EDIT: Guess you found it anyway.

---

