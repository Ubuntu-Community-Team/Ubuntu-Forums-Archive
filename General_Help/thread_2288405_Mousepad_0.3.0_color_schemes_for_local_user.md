---
title: "Mousepad 0.3.0 color schemes for local user"
date: 2015-07-27
forum: General Help
---

### Post by vasa1 on 2015-07-27
I installed Mousepad 0.3.0 on Lubuntu 14.04.

Mousepad allows the user to choose a color scheme. By default, these schemes are in */usr/share/gtksourceview-2.0/styles*.

After backing up cobalt.xml, I edited the file to tweak some colors using *sudo nano*. That was successful.

But I prefer to make changes as a local user rather than system-wide. So I copied the styles folder over to ~/.local/share/gtksourceview-2.0 and then edited cobalt.xml. But those changes don't seem to have any effect. It appears that Mousepad isn't seeing *~/.local/share/gtksourceview-2.0/styles*? Is that correct or do I need to place the styles folder somewhere else?

---

### Post by Toz on 2015-07-27
It looks like its maybe a bug of gtksourceview2, unless its intended to work like this. According to the [spec]("https://wiki.gnome.org/Projects/GtkSourceView/StyleSchemes"), it doesn't really define how the style search path works. Does it overwrite or does it append?

Using either mousepad or gedit, the style doesn't change if you place an edited copy with the same name of the file in ~/.local/share/gtksourceview-2.0. 

If you rename the local version (and change the style_scheme_id line), then it works (but it now has a different style name).

---

### Post by vasa1 on 2015-07-27
> **Toz said:**
>  ...
If you rename the local version (and change the style_scheme_id line), then it works (but it now has a different style name).
That did it. :) Thank you very much :)

---

