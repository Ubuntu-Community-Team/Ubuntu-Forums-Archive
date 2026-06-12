---
title: "why does ubuntu miss important mouse settings?"
date: 2015-02-13
forum: General Help
---

### Post by ramas2 on 2015-02-13
hi
may i ask why does ubuntu miss important mouse settings?

i download the last built 64bit
i installed and i can not select the direction of the mouse wheel scrolling ,clockwise counterclockwise
and i can't select how pages should the mouse wheel should scroll


thanks

---

### Post by kerry_s on 2015-02-13
i blame the mouse, if only it was built for linux instead of those other os's. :)

---

### Post by ramas2 on 2015-02-13
> **kerry_s said:**
> i blame the mouse, if only it was built for linux instead of those other os's. :)

i mean can't find these settings :(

---

### Post by kerry_s on 2015-02-13
> **ramas2 said:**
> i mean can't find these settings :(

i know what you meant, it's just something you wouldn't normally change, even in windows you would need the manufactures drivers to do that.

if your using firefox, you can change the lines scrolled in "about:config" looks like default is 5. scroll direction i have no idea, i'm sure it can be done, i just don't know how.

---

### Post by Holger_Gehrke on 2015-02-13
You could use 'xinput' from the command line. 
```

xinput list

```
gives you the input devices and their ids.
```

xinput -get-button-map "put your mouse's id here"

```
gives you the current mapping of buttons to functions. The scroll wheel is seen as two button, number 4 and 5. By switching them around 
```

xinput -set-button-map "put your mouse's id here" 1 2 3 5 4 "put more buttons here if you have them ..."

```
you can invert the direction of mouse wheel scrolling.

How far an application scrolls if it gets these events from X is up to the program, which is why you can set it in firefox (and can't in most other apps).

---

### Post by kerry_s on 2015-02-13
lol
i just installed xubuntu & it has the scroll change direction you were looking for, so there must be a way to add it to ubuntu.

---

