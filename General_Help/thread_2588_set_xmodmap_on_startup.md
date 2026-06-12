---
title: "set xmodmap on startup"
date: 2004-10-29
forum: General Help
---

### Post by Pieter on 2004-10-29
I have a customized xmodmap in order to enable some extra mousebuttons.
In order to set it properly I created .xinitrc and placed in my home-dir.
However, it isn't executed, so I have to call xmodmap manually each time.

In which file should I place the call to xmodmap in order for the modmap to be set each time I login?

---

### Post by beesee on 2004-10-29
Try putting it in ~/.gnomerc (create it if it doesn't exist).

---

