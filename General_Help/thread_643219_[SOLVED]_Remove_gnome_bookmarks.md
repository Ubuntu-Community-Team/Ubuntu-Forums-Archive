---
title: "[SOLVED] Remove gnome bookmarks"
date: 2007-12-17
forum: General Help
---

### Post by nvteighen on 2007-12-17
Hi there!
I've got a strange issue. For some reason, GNOME doesn't want me to remove bookmarks from the Places menu. I've tried to remove them by deleting and also just blanking ~/.gtk-bookmarks, but each time I restart X, these bookmarks reappear!

Is there something I'm missing?

Thanks in advance!

---

### Post by nvteighen on 2007-12-19
OK, I've solved it by myself. I put the solution here so anyone else needing this can find it.

It's rather simple, it occurs with those GNOME new default folders called like "Documents" or "Music".  I've deleted some of them but others not, so I've got some of these folders marked up instead of all. To remove them from bookmarks permanently, do this:

1. open a Terminal (Applications --> Accessories) and type:
2. ```

gedit ~/.config/user-dirs.dirs

```
You may use your favorite text-editor, like vi, kate or nano...
3. There, you should set as "$HOME/" any of those default folders you don't want them to appear in bookmars. **Don't touch XDG_DESKTOP_DIR** (it would change your desktop folder and you may have some issues).

That's it.

---

### Post by Roo on 2008-07-15
This is also logged as a bug

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/38142](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/38142)

There is a GUI procedure that allows easy editing.  Simply open any of the bookmarks under your places menu (say the "Home Foldder" for example).  In the window that opens, use the Bookmarks menu to edit them.

Roo

---

