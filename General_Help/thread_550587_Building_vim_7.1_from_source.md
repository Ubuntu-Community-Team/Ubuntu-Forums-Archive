---
title: "Building vim 7.1 from source"
date: 2007-09-14
forum: General Help
---

### Post by horrendo on 2007-09-14
I'm trying to build vim 7.1 from source but my end result for gvim has no menu or toolbar buttons.

I use this command ...

./configure --enable-gui=gtk2 --with-features=big

I'm guessing that it is due to 1+ packages I'm missing.

This is what the standard ubuntu gvim shows ...

stbaldwin@au-stb-mobile:~/vim71/src$ gvim --version
VIM - Vi IMproved 7.0 (2006 May 7, compiled Aug 28 2007 18:26:04)
Included patches: 1-164, 234-235
Compiled by [email]buildd@rothera.buil[/email]dd
Big version with GTK2-GNOME GUI.  Features included (+) or not (-):
:

Here's what mine shows ...
stbaldwin@au-stb-mobile:~/vim71$ src/vim --version
VIM - Vi IMproved 7.1 (2007 May 12, compiled Sep 14 2007 16:20:28)
Compiled by stbaldwin@au-stb-mobile
Big version with GTK2 GUI.  Features included (+) or not (-):
:

Any clues as to what I did wrong or what I'm missing?

Thanks

---

