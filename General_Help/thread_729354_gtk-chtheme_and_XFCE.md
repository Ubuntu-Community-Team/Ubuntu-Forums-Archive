---
title: "gtk-chtheme and XFCE"
date: 2008-03-19
forum: General Help
---

### Post by Koori23 on 2008-03-19
Okay, I was playing in Fluxbox. I installed gtk-chtheme. I found out I don't like fluxbox.. Logged back into XUbuntu. Now, I can't change my themes without using gtk-chtheme. How do I revert back to using XFCE's standard theme changing app? I'm using Xubuntu 7.10

---

### Post by RedSquirrel on 2008-03-19
gtk-chtheme creates the file ~/.gtkrc-2.0. If you want to let Xfce handle the theming, you can get rid of that file:

```
rm ~/.gtkrc-2.0
```or you could simply rename the file:

```
mv ~/.gtkrc-2.0 ~/.gtkrc-2.0_old
```

---

