---
title: "longer desktop icon names"
date: 2020-02-16
forum: General Help
---

### Post by Skaperen on 2020-02-16
it appears that there is a limit of 8 characters for the names under the icons in my desktop.  i'd like to get longer names.  is there a way to do that?  idk but, this may be an xfce issue (i run xubuntu).  i have some names i'd like to use as long as 20 characters that if truncated to 8 characters would cause ambiguities and if trimmed on the front would cause some other ambiguities.

---

### Post by CatKiller on 2020-02-16
[https://git.xfce.org/xfce/xfdesktop/tree/README](https://git.xfce.org/xfce/xfdesktop/tree/README)

The bit that you're interested in is setting ```
XfdesktopIconView::ellipsize-icon-labels = 0
```

---

### Post by Skaperen on 2020-02-16
the file they refer to does not exist.  do i need to create the whole thing or just the parameters i'm changing?

---

### Post by CatKiller on 2020-02-16
I don't use Xfce, so I can't test it, but I'd imagine that ```
style "xfdesktop-icon-view" {
    XfdesktopIconView::ellipsize-icon-labels = 1

}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
``` 
would be sufficient, with defaults from wherever the system config file is. Maybe you'd need to play with the spacing ones if the potentially bigger text boxes affect that.

---

### Post by Skaperen on 2020-02-17
it works in that short form, after i changed the 1 to 0.

---

### Post by Skaperen on 2020-02-17
actually, the limit is 7.  but that could be because of the font size i have set.

---

