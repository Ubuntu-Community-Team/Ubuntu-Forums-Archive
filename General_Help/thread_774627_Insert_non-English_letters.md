---
title: "Insert non-English letters"
date: 2008-04-29
forum: General Help
---

### Post by ressaw on 2008-04-29
Hi, I write in Portuguese using an English keyboard and in Windows Vista (I think that in XP too) you can insert for example letter " ç " by pressing " ' " and then "c" or put accents on letters by pressing " ~ " and then " a " to obtain " ã ", but I don't know how to do this in Ubuntu because if I configure the keyboard as an English one, I get the things separated (like 'c and ~a), and if I set it in Portuguese the layout of the keyboard changes and I can't work. Thanks

---

### Post by jdimas on 2008-05-02
same problem, no solution

---

### Post by ressaw on 2008-05-03
Just as a side question: the feature for "ç" to appear when I press " ' " and then "c" is something new in vista or is an old windows feature?

---

### Post by ibuclaw on 2008-05-03
You could, for something temporary, use the ascii code to insert it.

ie:
"ã" is the character code 227 (I think).
And to write it out, holding Alt and typing the number should print the character on screen.

[EDIT]
[Read Here...]("http://www.starr.net/is/type/altnum.htm")
Portuguese is at the bottom.

Regards
Iain

---

### Post by ibuclaw on 2008-05-03
D'oh... Oops, just remembered.

The **Right-ALT** key (Also known as **Alt-Gr**) is used for these sorts of functions.

Now open up a text editor (gedit) and type in "**Alt-Gr+Shift+~**" followed by "**a**" and the letter "**ã**" appears (It works!)

Regards
Iain

---

### Post by scorp123 on 2008-05-03
> **ressaw said:**
>  Hi, I write in Portuguese using an English keyboard ... but I don't know how to do this in Ubuntu because if I configure the keyboard as an English one, I get the things separated (like 'c and ~a) You have to select this layout: "US International" .... then it will work again the same way as e.g. in Vista and you will be able to write European accentuated characters by combining the necessary keys.

Wikipedia article explaining the layout:
[http://en.wikipedia.org/wiki/Keyboard_layout#US-International](http://en.wikipedia.org/wiki/Keyboard_layout#US-International)

---

### Post by jdimas on 2008-05-03
I use a brazilian abnt2 keyboard and ubuntu in english, and I don't have any interest in using ubuntu in portuguese.
In gutsy I didn't have any problems, just selected the abnt2 keyboard and english language during the installation with the live cd... In hardy, the same procedure did not work well.
I googled and searched the forum but I haven't found any solution.
Thanks!

---

### Post by jdimas on 2008-05-04
I just made it work.
In "System > Preferences > Keyboard" I changed the keyboard model (to a generic one), added a new layout (again, anyone you want), deleted brazilian layout, and then I changed the model back to "Brazilian ABNT2", and added the Brazil "default" layout.
Now I can put "~^" and other characters over the vowels again.
Hope it helps.

---

