---
title: "Remap right control to super using Xmodmap"
date: 2013-09-19
forum: General Help
---

### Post by josephellengar2 on 2013-09-19
I'm having a little bit of trouble with Xmodmap. How do I remap might right control (keycode 105) to Super? One of the problems is that when keycode 105=Super_R, Xmodmap also changes the left control (keycode 37) to be a super. I guess it has something to do with clearing control entirely and remapping the left, but I'm not sure.

This is my entire .Xmodmap file right now:

```

keycode 66 = Super_L
clear Lock

```

---

