---
title: "Changing Icon Themes in Thunar?!"
date: 2008-05-28
forum: General Help
---

### Post by HangukMiguk on 2008-05-28
I'm in Openbox, trying to switch the icon theme in thunar.  I don't even know if I extracted to the right place, but when I use the XFCE User Interface Preferences to switch icon themes, it obviously doesn't do anything, since I'm in *box.

I'm clearly probably going to have to do this manually.  Where should I extract my icons to, and how should I change the theme in Thunar?

---

### Post by urukrama on 2008-05-28
> **HangukMiguk said:**
> I'm in Openbox, trying to switch the icon theme in thunar.  I don't even know if I extracted to the right place, but when I use the XFCE User Interface Preferences to switch icon themes, it obviously doesn't do anything, since I'm in *box.

I'm clearly probably going to have to do this manually.  Where should I extract my icons to, and how should I change the theme in Thunar?

The Xfce User interface preferences (xfce-setting-show) *can* be used to change the Gtk and icon theme in Openbox. You need to extract the icon theme in ~/.icons or /usr/share/icons

You can also set the icon theme in the ~/.gtkrc-2.0 or ~/.gtkrc.mine file. See [here]("http://urukrama.wordpress.com/openbox-guide/#Gtkthemes") for more info.

---

### Post by HangukMiguk on 2008-05-28
> **urukrama said:**
> The Xfce User interface preferences (xfce-setting-show) *can* be used to change the Gtk and icon theme in Openbox. You need to extract the icon theme in ~/.icons or /usr/share/icons

You can also set the icon theme in the ~/.gtkrc-2.0 or ~/.gtkrc.mine file. See [here]("http://urukrama.wordpress.com/openbox-guide/#Gtkthemes") for more info.
Ok, I've done this, but whenever I open Thunar after changing the settings in xfce-setting-show, it still shows up with the Human icon theme.

---

### Post by HangukMiguk on 2008-05-28
hrm...I had a fit of dumb brilliance, switched to gnome for a sec, and changed the icon theme in there (trying to do so in Openbox with the gnome display preferences manager switched everything to gnome).  I switched back to openbox, and sure enough, thunar is themed right.

Thanks though Urukrama (seriously, if not for your howto on openbox, i'd be lost in this thing).

---

