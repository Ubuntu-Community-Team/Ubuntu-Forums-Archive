---
title: "Expected visual behavior of notifications (gnome metacity)"
date: 2013-11-04
forum: General Help
---

### Post by helloworld1215 on 2013-11-04
I sometimes see notification popups on the right of the  screen that specify things like network connectivity status changes  mainly. 
  I don't understand their expected visual behavior in that:
  
[LIST=1]
[*]It would appear that sometimes, when you move your mouse close to them, they disappear to reappear when you move away.
[*]It does not appear to be possible to ever click on them or hide them  in any way, they generally just flicker, often in a in determinant way.
[*]Is the flickering perhaps caused because every flicker is in fact a unique notification?
[/LIST]

---

### Post by 3rdalbum on 2013-11-04
If you are using a composited window manager with 3D acceleration (such as Unity 3D) the notifications will smoothly fade out as you approach them, to convey that you can click on whatever is sitting behind them. Without compositing or 3D acceleration, the notification will simply disappear temporarily as it's not possible to fade it out.

Ubuntu has designed its notifications to not demand interaction from the user, that's why you don't click on them to hide them. Just wait a few seconds and they go away on their own.

---

