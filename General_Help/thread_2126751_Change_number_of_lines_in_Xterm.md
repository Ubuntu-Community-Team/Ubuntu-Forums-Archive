---
title: "Change number of lines in Xterm"
date: 2013-03-18
forum: General Help
---

### Post by Alaza on 2013-03-18
Hi guys.

Is it possible for me to change the number of lines in the Xterm window? So that there is a higher or no limit on the length of the scroll bar so to speak.

Thank you

Tore.

---

### Post by sudodus on 2013-03-18
> **Alaza said:**
> Hi guys.

Is it possible for me to change the number of lines in the Xterm window? So that there is a higher or no limit on the length of the scroll bar so to speak.

Thank you

Tore.

Yes, a lot is possible with xterm. See ```
man xterm
```

example: a window with 200 character line length (window width) and 10 lines (window height)
```
xterm -geometry 200x10
``` while
```
xterm -geometry 80x25-50-50
``` puts the window near the right lower corner
+ distance in pixels from left/upper
- distance in pixels from right/lower

---

### Post by Alaza on 2013-03-18
> **sudodus said:**
> Yes, a lot is possible with xterm. See ```
man xterm
```

example: a window with 200 character line length (window width) and 10 lines (window height)
```
xterm -geometry 200x10
``` while
```
xterm -geometry 80x25-50-50
``` puts the window near the right lower corner
+ distance in pixels from left/upper
- distance in pixels from right/lower

I'm not sure I made myself clear enough. :)

I can understand that it's possible to use scrolllines as an argument to they keyboard shortcut assigned to open Xterm. However, I'm not quite sure how to do it. When in Settings Manager -> Keyboard -> Application Shortcuts I previously had "xterm -ls" assigned for a specific key. But how do I give it an argument with scrolllines?

---

### Post by sudodus on 2013-03-18
> **Alaza said:**
> I'm not sure I made myself clear enough. :)

I can understand that it's possible to use scrolllines as an argument to they keyboard shortcut assigned to open Xterm. However, I'm not quite sure how to do it. When in Settings Manager -> Keyboard -> Application Shortcuts I previously had "xterm -ls" assigned for a specific key. But how do I give it an argument with scrolllines?
So you want to scroll rather than have a big window? Then use -sb to get a scrollbar, and to get it at the right side, use
```
xterm -sb -rightbar
``` and scroll with the middle button.

I'm not sure, but I think that bash sets the number of lines to be saved (and possible to scroll).

---

