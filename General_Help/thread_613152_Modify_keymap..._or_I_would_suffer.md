---
title: "Modify keymap... or I would suffer"
date: 2007-11-14
forum: General Help
---

### Post by benton on 2007-11-14
Hi there! I had this great idea... to purchase keyboard stickers for my language and affix them to my English keyboard laptop so I can have the keyboard in my native language. Turns out, now I don't have a key with the "<" and ">" characters on the keyboard. Gosh I feel dumb... LOL.

But I've noticed that I can type other extended characters by using the "Alt Gr" key combined with other key, for instance, Alt Gr + z gives me "«" and Alt Gr + x gives me "»".   

So is there a way I can change this to get the "<" and ">" working again? Can I edit the current keymap to accomplish this?

Thanks for any solutions,

-Benton

---

### Post by benton on 2007-11-15
*bump*

Anyone please?

---

### Post by JasonF on 2007-11-15
xmodmap provides a method to edit the current key map for a session.

Try running xev and punching the key you want to redefine in the window, look at the terminal and note the keycode value.  Run xmodmap like 

xmodmap -e "keycode 24 = q Q < >"

which would set the key Q (keycode 24) to use  q and Q like normal, < and > would be output when when the Alt Gr modifier or both shift and Alt Gr are pressed.

---

