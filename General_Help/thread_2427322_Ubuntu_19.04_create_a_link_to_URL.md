---
title: "Ubuntu 19.04 create a link to URL"
date: 2019-09-20
forum: General Help
---

### Post by Edward_Diener on 2019-09-20
Evidently in Ubuntu 19.04 it is no longer possible to drag a link from a web browser, such as Firefox, into a folder, so that when I double click the link the web page in my default web browser opens. Since I can not do this by drag and drop how can I manually create such a link inside a Nautilus ( or Nemo ) folder ?

---

### Post by Holger_Gehrke on 2019-09-20
If I grab the link "General Help" from above and drag it into a Thunar window on my XUbuntu 18.04 a .desktop-file (which is just a text-file with the extension ".desktop" and the right structure ...) is created with this content:
```

[Desktop Entry]
Version=1.0
Type=Link
Name=General Help
Comment=
Icon=user-bookmarks
URL=https://ubuntuforums.org/forumdisplay.php?f=331

```
You could try to use this as a template and see whether it works.

Holger

---

### Post by #&amp;thj^% on 2019-09-20
For Nemo,
1. If your Mouse Has a Center Button

You just Center-Click and drag the file to where you want it to go, and when you release the center-button/wheel, a menu will pop up asking you if you want to Move, Copy, or Link the file.

Choose Link, of course.
2. If Your Mouse DOESN'T Have a Center Button

You Left-Click and drag the file to where you want it to go, but right before you release the left-button, **hold down the Alt key**, then release the left-button, and a menu will pop up asking you if you want to Move, Copy, or Link the file.

Choose Link, of course.

---

### Post by Edward_Diener on 2019-09-20
> **1fallen said:**
> For Nemo,
1. If your Mouse Has a Center Button

You just Center-Click and drag the file to where you want it to go, and when you release the center-button/wheel, a menu will pop up asking you if you want to Move, Copy, or Link the file.

Choose Link, of course.
2. If Your Mouse DOESN'T Have a Center Button

You Left-Click and drag the file to where you want it to go, but right before you release the left-button, **hold down the Alt key**, then release the left-button, and a menu will pop up asking you if you want to Move, Copy, or Link the file.

Choose Link, of course.

No menu popped up but it automatically created a link, which is what I wanted. Thanks !

---

### Post by #&amp;thj^% on 2019-09-20
Awesome, and glad that worked out.

---

