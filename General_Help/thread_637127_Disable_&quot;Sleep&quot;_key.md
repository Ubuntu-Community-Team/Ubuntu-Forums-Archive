---
title: "Disable &quot;Sleep&quot; key?"
date: 2007-12-10
forum: General Help
---

### Post by schmolch on 2007-12-10
Its really great that all my keyboard's special keys work out of the box but not so regarding the sleep-key, which puts the desktop to sleep wthout asking for confirmation.

It must be preconfigured somewhere but its not part of the gnome keyboard preferences like all the other special keys.

Where can i delete the configuration for the sleep key?

---

### Post by Solicitous on 2007-12-11
If you open up a terminal and run gconf-editor.  Go to apps > gnome-power-manager > buttons.  There should be 5 or so keys.  Edit the Power key and change it's value to **nothing** (Actually type in the word nothing)
Close gconf-editor and all should be good.

---

### Post by schmolch on 2007-12-11
That did it, thanks alot!

---

