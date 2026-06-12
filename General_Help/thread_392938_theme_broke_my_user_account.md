---
title: "theme broke my user account"
date: 2007-03-25
forum: General Help
---

### Post by Obor on 2007-03-25
I was playing around on my edgy install yesterday and clicked on some icons (don't remember the name) in my themes manager. and everything froze.

I tried restaring but it stops at the splash screen and then nothing. Which folder/files should i delete and/or copy over from my other user account to fix this? i.e. How to change the theme to the same as other user or default without going to the theme manager?

Any ideas? It took me a while to customize my account the way I want...

---

### Post by bapoumba on 2007-03-25
Hello,
look in your user ~/.themes if you recognize the theme name you were using and rename it. The default theme should be used next time you log in.
If this does not work, you can also rename the .gconf in .gconf_old, a new one will be created on login. You may lose some customizations though.

---

### Post by Obor on 2007-03-25
> **bapoumba said:**
> If this does not work, you can also rename the .gconf in .gconf_old, a new one will be created on login. You may lose some customizations though.

That has sorted me out. Thanks :)

---

