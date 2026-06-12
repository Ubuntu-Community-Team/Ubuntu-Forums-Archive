---
title: "Nautilus configuration"
date: 2007-04-24
forum: General Help
---

### Post by CocoAUS on 2007-04-24
I just did a clean install of Feisty, and I can't remember how I got Nautilus to show navigation buttons with the text besides the buttons.  Can anyone help me out here?  If it's in gconf-editor (which it probably is), I'm having a horrible time finding it.  Thanks ahead of time!

---

### Post by Ziggy72 on 2007-04-24
Sorry, but I don't really understand what you want. If you're more specific then maybe I or somebody else can help.

As a rather wild guess, maybe you want to show the location entry as text in Nautilus, rather than the default icons. If that is indeed what you want to do then in a terminal type ```
gconf-editor
``` and then go to apps > nautilus > preferences and tick "always_use_location_entry".

---

