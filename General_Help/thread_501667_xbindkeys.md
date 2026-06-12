---
title: "xbindkeys"
date: 2007-07-15
forum: General Help
---

### Post by PurposeOfReason on 2007-07-15
Today I was messing around with xbindkeys to get the left thumb buttons on my mouse to work as forward and back with FF. While every tutorial or thing I tried worked it also enabled me clicking the mouse wheel to go back a page instead of open in new tab, like it used to do. Just to prevent this I gave it a task it can't do so my .xbindkeys looks like 
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[PageDown]""
  m:0x0 + b:2

```
The last one being the scroll click. Is there a command I can give it so it goes back to opening links in a new tab without taking me back a page?

---

### Post by dagnabit dang doohickey on 2007-07-15
Try replacing "\[Alt_L]\[PageDown]" with "\[Control]\[t]"

---

### Post by PurposeOfReason on 2007-07-15
That makes it open a new blank tab but not the link I click on. The keyboard shortcut for it is ctrl+shift+left click. I just don't know how I'd put that.

---

### Post by avik on 2007-07-15
While xbindkeys has worked great for keyboard events, I prefer [btnx]("http://ubuntuforums.org/showthread.php?p=3009512") for mouse events.  It works all across the desktop, so I can use my other mouse buttons even in nautilus.

---

### Post by dagnabit dang doohickey on 2007-07-15
I'm winging it now with: "\[Control]\[Shift]\[b:1]"

That probably won't work. This might:

"\[Control]\[Shift]\[mouseclick 1]"

---

