---
title: "Emacs loads slowly with diff font"
date: 2007-01-16
forum: General Help
---

### Post by eitan_a on 2007-01-16
Hey guys.  I'm running Ubuntu 6.10 on a fast Sony Vaio laptop.

Emacs loads very quickly when I don't set any fonts in .emacs.  However, the font is a bit big and I need something smaller to conserve my desk space.  The problem is if I set a different default font, emacs takes an extra 5 seconds to load which is a lot more annoying than it sounds.  Do I need to install some fonts or do some mods to emacs?  The font does load, but the loadup time is long.

I've tried different fonts and they all load slowly.  Any help appreciated.  I want to use this font..

   (set-default-font "-adobe-courier-medium-r-normal--14-100-100-100-m-90-iso10646-1")

Thanks!

---

### Post by jshipley on 2007-01-19
I'm having the same problem since upgrading to Edgy.  When I open emacs, it has a really small ugly font.  If I open it with a --font 9x15 then the font looks fine and emacs opens quickly.  If I set the font via .emacs then it takes a few seconds to open.  Very annoying.

* Update
Running on a Dell Inspiron 9300

---

