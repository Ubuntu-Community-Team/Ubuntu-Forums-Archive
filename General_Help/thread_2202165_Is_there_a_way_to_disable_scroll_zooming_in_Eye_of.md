---
title: "Is there a way to disable scroll zooming in Eye of Gnome Image Viewer?"
date: 2014-01-27
forum: General Help
---

### Post by ggodone on 2014-01-27
I'd really like to have an intermediate image viewing applications between previewing in sushi and opening in GIMP, like Preview is in OS X. The default GNOME 3 image viewer Eye of Gnome seems like a good replacement (besides the lost functionality of copying and pasting images in and a cumbersome way to access the advanced edit tools), but the fact that scrolling zooms instead actually scrolling (like every single other app in existence) makes it unusable. Is there a way to have normal scroll behavior in it?

---

### Post by ibjsb4 on 2014-01-27
Looks like dconf-editor can do that.

[ATTACH=CONFIG]249791[/ATTACH]

You may need to install it.

```
sudo apt-get install dconf-tools
```

---

### Post by ggodone on 2014-01-28
Thank you! Now I'll be able to use it :P

---

