---
title: "Customized modifier keys"
date: 2007-08-17
forum: General Help
---

### Post by Dingbats on 2007-08-17
I want to customize my own keyboard layout to make it easier to type certain characters. I know about the layout files in /usr/share/X11/xkb/symbols, but what I want to do is this, and I'm not sure you can do it by editing those files:

-- Left and right alt should work the same way. I want to be able to type characters like [ ] { } | etc with both of them (sometimes combined with shift).
-- The super keys should work as extra modifier keys. So you would be able to combine the alt, shift and super keys to type lots and lots of crazy characters.
-- Some keys should act as dead keys, for example if I press the key next to backspace and then a, I would get a-acute.

How do I do that?

---

### Post by Dingbats on 2007-08-20
Bumpity bump... :S

---

### Post by Dingbats on 2007-08-21
I have looked in the files in /usr/share/X11/xkb/symbols, and I think I got how they're structured; the first symbol code in each group is a normal press, the second is with alt, etc. But how do I change which key causes another symbol to be chosen? I want left alt to trigger the second symbol in each group as well as the right alt. I also want to add other symbols triggered by the super keys.

An example of a key code with four symbols picked depending on modifier keys pressed:
```
    key <AD07>	{ [         u,          U,    downarrow,      uparrow ]	};
```
I could just change the values of those four variables, but that wouldn't make the left alt key behave differently...

---

### Post by Dingbats on 2007-08-22
Ok, so I've messed around a bit with xmodmap, but all I've managed to do is accidentally remapping the a key to b (managed to fix it though). When I remapped keycode 64 (left alt) to ISO_Level3_Shift (what xev returns for right alt), none of them would work at all anymore.

So I really need some help with this... please...

---

### Post by Dingbats on 2007-08-22
Dang! I can't believe I didn't check the obvious. It's right there in the keyboard settings!#-o

---

