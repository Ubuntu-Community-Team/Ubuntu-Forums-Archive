---
title: "Stop terminal from &quot;live-updating&quot;?"
date: 2013-02-05
forum: General Help
---

### Post by Alaza on 2013-02-05
Hi guys.

I'm wondering, is it possible somehow to stop the terminal from live updating? By this I mean that for instance when I'm running a bzr commit with a lot of files, it's impossible to scroll in the terminal, as I'm constantly thrown to the bottom for each increment of the update.

Is it possible to disable this feature?

---

### Post by 3rdalbum on 2013-02-05
There must be a way. If you pipe the output through Less, does this work well enough?

---

### Post by Calinou on 2013-02-05
The Xfce terminal can do that (and you can install it in any desktop environment), install the "xfce4-terminal" package.

---

### Post by The Cog on 2013-02-05
If it's gnome-terminal:
menu **Edit** / **Profile Preferences**, go to the **Scrolling** tab and un-check **Scroll on output**.

---

