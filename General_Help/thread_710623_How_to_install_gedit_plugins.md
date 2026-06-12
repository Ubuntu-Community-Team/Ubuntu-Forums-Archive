---
title: "How to install gedit plugins?"
date: 2008-02-28
forum: General Help
---

### Post by Ultra Magnus on 2008-02-28
This is probably a bit of a silly question but how do you install gedit plugins - I mean ones which aren't distributed with gedit or in the repositories.

Theres nothing on the gedit website although a bit of a search suggested extracting it to ~/.gnome2/gedit/plugins ~/.gnome2/gedit or ~/.gnome2/plugins  - I tried all of those but no luck - I can't seem to find any way of doing it - any ideas?

Thanks,

Jim

---

### Post by ayoli on 2008-02-28
.gnome2/gedit/plugins/ is the right directory (or /usr/lib/gedit-2/plugins/ if you want them wide installed).
Your plugin should have a <name_of_plugin>.gedit-plugin file and a <name_of_plugin>.py file or a folder containing .py files with maybe a glade file.
the <name_of_plugin>.gedit-plugin must be in the root of the plugins directory (e g: .gnome2/gedit/plugins/).
If it still doesn't work try to run gedit from a terminal and look at the output, you may find some useful debug info.

---

