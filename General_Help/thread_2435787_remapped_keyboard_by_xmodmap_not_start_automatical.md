---
title: "remapped keyboard by xmodmap not start automatically"
date: 2020-01-26
forum: General Help
---

### Post by abdulbadii on 2020-01-26
I have latest Lubuntu (eoan)  with mate DE, and need the remapped keys so having:
```

$ cat ~/.Xmodmap
keycode  90 = Tab NoSymbol Tab
keycode 104 = KP_Insert NoSymbol KP_Insert
keycode 86 = Escape

```
and made one there too:
```

$  cat ~/.xinitrc
xmodmap ~/.Xmodmap



```
but this autostart doesn't work every time I login / (re)start PC
so every then I have to open terminal and type ```
xmodmap ~/.Xmodmap 
``` <enter>
which then is working.

What should I do to solve this?
Thanks before.

---

### Post by vanadium on 2020-01-26
You could try whether introducing a little delay may help, e.g. "sleep 3 && xmodmap ~/.Xmodmap" to have a 3 second delay before xmodmap is executed. Alternatively, try whether using the autostart system of Lubuntu desktop to execute this command is more reliable.

---

