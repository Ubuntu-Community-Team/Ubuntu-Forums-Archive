---
title: "Disable XGL for 3D applications?"
date: 2007-11-16
forum: General Help
---

### Post by Sparky222B on 2007-11-16
I'm using 7.10, and I'd like a way to quickly kill/start XGL+Compiz so that I can use OpenGL direct rendering with fgrlx.

Any ideas?

---

### Post by neko18 on 2008-02-02
To disable Compiz:
```
metacity --replace
```

To re-enable Compiz:
```
compiz --replace
```

If you would like to make a script to launch the application with Compiz disable, here is an example with the game Glest:
```
#!/bin/sh
metacity --replace &
glest
compiz --replace &
```
To use it, just save it to somewhere like ~/bin or ~/.local/bin, make it executable, then point the appropriate menu shortcut to it.

---

### Post by NineseveN on 2008-02-02
Solution here: [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

---

