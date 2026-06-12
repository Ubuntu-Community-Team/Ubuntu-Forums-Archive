---
title: "Fullscreen, no borders?"
date: 2006-12-29
forum: General Help
---

### Post by mhueting on 2006-12-29
Hi,

I would like to be able to work in vim full screen, without the window borders. I don't know if it is possible, but anyhow, it would rock :D

Thanks :D

---

### Post by mhueting on 2006-12-29
Solved it.

I first fired up devilspie in debug mode, so everytime I opened a program I'd see what the appname was. The name for GVim was Vim, so this was the code:

(if (is (application_name) "Vim") (begin (set_workspace 1) (undecorate) (maximize) ) )

and that's it :D

Works great, and looks even better ;)

---

