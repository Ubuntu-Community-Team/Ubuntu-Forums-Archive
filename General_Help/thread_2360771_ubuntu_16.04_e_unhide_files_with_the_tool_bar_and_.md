---
title: "ubuntu 16.04 e unhide files with the tool bar and not by ctrl h"
date: 2017-05-08
forum: General Help
---

### Post by pagno2 on 2017-05-08
Hello
Ubuntu 16.04, pretty sure I have Unity and not GNOME.
In Ubuntu 17.04 I could hide/unhide files clicking on the second toolbar button from the right.
Now no window pops up after clicking the "list" button o f the tool bar and I have to do it by ctrl + h.
GA

---

### Post by howefield on 2017-05-08
> **pagno2 said:**
> Ubuntu 16.04, pretty sure I have Unity and not GNOME.

```
echo $XDG_CURRENT_DESKTOP
```

should return Unity:Unity7 if that is what you are running.

> In Ubuntu 17.04 I could hide/unhide files clicking on the second toolbar button from the right. Now no window pops up after clicking the "list" button o f the tool bar and I have to do it by ctrl + h.

What's the question ?

You are describing expected default behavior for the respective versions of Ubuntu/Files. In 16.04 you have the View menu option to show/hide hidden folders and which is now integrated into the Files menu bar in 17.04.

---

### Post by pagno2 on 2017-05-08
thanks
1. Unity
2. I probably didn't write properly. The issue is: I can hide/unhide files using ctrl H, but I would like to do it using the tool bar. I remember I could use the [COLOR=#111111][FONT=Ubuntu]checkbox "[/FONT][/COLOR]Show hidden files". Now no checkbox appears when clicking on the "view item as a list" toolbar button.
GA

---

### Post by pagno2 on 2017-05-08
sorry I was trying to change the spelling error in the title and I marked it as solved. It is not.
GA

---

### Post by again? on 2017-05-08
This is what I see in Files on Ubuntu-Gnome 17.04.
In earlier versions you need to use the view menu in the title bar or unity panel.
If you want more customization in your file browser I suggest installing nemo.

---

