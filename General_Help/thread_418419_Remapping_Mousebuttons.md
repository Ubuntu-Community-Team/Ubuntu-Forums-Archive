---
title: "Remapping Mousebuttons"
date: 2007-04-22
forum: General Help
---

### Post by willywilly on 2007-04-22
I just connected a Logitech mouse to my PC and did this tutorial to successfully get the buttons to work:
[http://ubuntuforums.org/showthread.php?t=401710](http://ubuntuforums.org/showthread.php?t=401710)
(actually step 2 was all I needed)

Now I want to remap button 6 to Ctrl+Alt+Left  and button 7 to Ctrl+Alt+Right. I tried adding any of the following lines to ".xbindkeysrc", but none changed the behavior of those buttons.
> "/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Alt_L]\[left]"" 
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[left]"" 
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Alt_L]\[left]"" 

What am I doing incorrectly?

---

### Post by willywilly on 2008-03-08
I still havent figured this out. :/

---

