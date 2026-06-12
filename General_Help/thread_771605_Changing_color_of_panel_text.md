---
title: "Changing color of panel text"
date: 2008-04-27
forum: General Help
---

### Post by Mongoose.wa on 2008-04-27
In Feisty and Gutsy, I'd used [this guide]("http://brentroos.com/2006/07/07/change-gnome-panel-text-color/") to change the default font color of the top GNOME panel. Uncommenting the line in .gtkrc-2.0 has no effect in Hardy, however. What's the deal and how do I change the font color?

Thanks!

---

### Post by FuturePilot on 2008-04-27
The easiest way would be to probably use gnome-color-chooser
```
sudo apt-get install gnome-color-chooser
```

---

### Post by Mongoose.wa on 2008-04-27
> **FuturePilot said:**
> The easiest way would be to probably use gnome-color-chooser
```
sudo apt-get install gnome-color-chooser
```

I tried that. What do you style to change the text color? Panel foreground color doesn't do anything.

---

### Post by FuturePilot on 2008-04-27
Panel Foreground works here. Make sure you hit Apply.

---

### Post by Mongoose.wa on 2008-04-27
> **FuturePilot said:**
> Panel Foreground works here. Make sure you hit Apply.

No dice. Could something be overriding it?

---

### Post by Mongoose.wa on 2008-04-28
How do I set GNOME Color Chooser up to begin with? If I go to Help > Information, it lists:

Environment variables:
  GTK_PATH is not set.
  GTK_EXE_PREFIX is not set.
    GTK+ will search: $libdir/lib/gtk-2.0/...
  GTK_DATA_PREFIX is not set.
    GTK+ will search: $prefix/share/themes
  GTK2_RC_FILES is not set.
    GTK+ will read: $sysconfdir/gtk-2.0/gtkrc and ~/.gtkrc-2.0

---

### Post by nbayiha on 2008-04-28
Dude just use gnome-color-chooser like future pilot told u, and if u can do it with that means u have a problem , try to open with a terminal and post hear what it written when u try to apply.

---

### Post by Mongoose.wa on 2008-04-28
> **nbayiha said:**
> Dude just use gnome-color-chooser like future pilot told u, and if u can do it with that means u have a problem , try to open with a terminal and post hear what it written when u try to apply.

I did. And it did nothing.

When I run it in the terminal, it doesn't output anything when I hit apply.

```
Welcome to gnome-color-chooser version 0.2.3 for i486-pc-linux-gnu

Loading GUI with libglade.. /home/evan/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant
done
Initializing and starting gnome-color-chooser.. done
```

---

