---
title: "Middle mouse button to act as a keyboard key press"
date: 2015-02-28
forum: General Help
---

### Post by derek29 on 2015-02-28
Ubuntu 12.04.4
 
I would like to make it so **clicking the middle mouse button** behaves as though I pressed the **Escape key** on the keyboard.    
 
There’s plenty of examples of how to make a keyboard key behave as a moue button, which is not what I am interested in.
 
There doesn’t seem to be a way using xmodmap.  Xbindkeys seems more relevant to having a key-press perform an action rather than a remap.
 
Does it involve xbindkeys with xte?
 
# 3rd mouse button
"xte 'Escape'"
   b:3
 
This doesn’t seem to work.  Please advise.

---

### Post by derek29 on 2015-02-28
I had to install x virtual keyboard "xvkbd".

Put this in .xbindkeysrc

"xvkbd  -text "\e""
       m:0x0 + b:3

Then, reboot the entire system.  Trying to restart xbindkeys fails to restart even though it was previously running.    Glitchy, but this is working now.

---

### Post by CantankRus on 2015-02-28
As you appear to prefer using the mouse, you may find easystroke mouse gestures useful.
Bind commands, keystrokes to gestures or mouse buttons.

With easystroke you can keep middle click paste and bind the escape key 
to a **long** middle click or bind it to a gesture.
[http://ubuntuforums.org/showpost.php?p=10495426&postcount=11](http://ubuntuforums.org/showpost.php?p=10495426&postcount=11)

---

