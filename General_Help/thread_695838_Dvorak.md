---
title: "Dvorak"
date: 2008-02-13
forum: General Help
---

### Post by malfist on 2008-02-13
I found this code to switch to dvorak layout
```

setxkbmap dvorak &

```
But how do I switch back?
I've added the System->Pref->Keyboard and the Dvorak map but Ican't get it to activate. The only way I've found to get it off dvorak is to restart X.

---

### Post by spupy on 2008-02-13
There should be a Gnome program for switching keyboard layouts. Check the control panel. 
Try
```
setxkbmap us
```
?

---

### Post by xarquid on 2008-02-13
Set it back to what? :-)

[http://www.xfree86.org/current/setxkbmap.1.html](http://www.xfree86.org/current/setxkbmap.1.html)
Is a page explaining the options.

But if English I believe you want:

> setxkbmap us &

Sincerely,

Craig Huffstetler / xq / xarquid
Ubuntu SC / #ubuntu-us-sc

---

### Post by Trail on 2008-02-14
You can use the Keyboard preferences to set a dvorak layout. Then you can use a button-combination to switch, like Alt-Shift for me.

---

